# ios-knowledge

Some summaries of iOS knowledge points

[TOC]

> refer：https://www.jianshu.com/p/6b23e809e322
>
> 原文没有答案，我就尝试回答一下，有空就更新，欢迎各路大神不吝赐教。

## Swift和[C]的区别

- 协议

  - [C] 定义属性、方法等，类似接口。协议可以被继承，多继承

- ```objective-c
  @protocol NSObject

  - (BOOL)isEqual:(id)object;
  @property (readonly) NSUInteger hash;
  - (BOOL)isProxy;

  @end
  ```

  - Swift 包含[C]协议的所有功能；

    ​	   此外协议可以被应用于泛型；可以扩展协议，在扩展中自定义方法或给协议中的方法提供默认实现

    ```swift
    protocol Animal {
        func walk()
        var name: String { get set }
    }

    extension Animal {
        func walk() {
            // 默认实现
        }

        func anotherFunction() {
            // 添加新的方法
        }
    }
    ```



- 泛型

  - [C] 不支持

  - Swift 一大亮点，更安全的泛型；弱化的契约编程，可以指定泛型的基础类型。

- 结构体、类

  - [C]	**结构体**就是C语言的东西，属于值类型，由编译器管理生命周期。~~由于结构体没有析构函数（C++中的结构体如果包含方法就会升级为C++类），所以结构体不能含有[C]对象，因为编译器不知道在什么地方release对象才好。~~<sup><a href="arc-forbids-objective-c-objects-in-struct">[1]</a></sup>

    ​	**类**是包含了一个runtime的C的结构体，属于指针类型，采用引用计数管理生命周期。

  - Swift 也有结构体和类的区别。和[C]一样，结构体是值类型，类是指针（引用）类型。但Swift中结构体更强大，除了不能被继承、没有析构函数（deinit）外拥有类的所有功能。

- 类型安全

  - [C]	[C]的对象在编译期都可以被看作id类型，一个方法的参数需要接收类型A，在直接调用的地方也确实传了类型A的对象，但是有时候这个对象来自外部，而外部有可能莫名其妙传了一个类型B进来，编译的时候有可能还通过了，导致在运行时会出现找不到某某方法的selector而崩溃。

  - Swift 强静态类型语言，A就是A，B就是B，不会出现C/C++的隐式转换。

    ```swift
    let a = 1.23 // Double类型
    let b: Int = a // ❌ 无法直接从Double转换成Int，需要通过构造函数 Int(a)才行
    ```

> <a name="arc-forbids-objective-c-objects-in-struct">[1] 在Apple LLVM version 10.0.0 (clang-1000.11.45.5)中，C结构体可以包含ARC对象</a>
>
> 另见StackOverflow上的讨论：https://stackoverflow.com/questions/28471855/does-objective-c-forbid-use-of-structs

## 2、编译链接

## 3、synthesize & dynamic

## 在项目开发中常用的开发工具有哪些？

- charles 抓包，充当开发初期的mock工具。
- Xcode Document，查看API😼
- Git，版本管理

## 5、UITableView & UICollection

## 6、NSProxy & NSObject

## 7、Object & Swift

## 8、传值通知 & 推送通知（本地&远程）

## 9、第三方库 & 第三方平台

## 10、NSCache & NSDcitionary

## UIView的setNeedsDisplay和setNeedsLayout方法

|                  | setNeedsDisplay | setNeedsLayout                                               |
| ---------------- | --------------- | ------------------------------------------------------------ |
| 同步/异步        | 异步            | 异步                                                         |
| 实际会调用的方法 | drawRect        | layoutSubviews                                               |
| 作用             | 绘制界面        | （非自动布局的情况下）调整子控件的布局，此时的控件frame确定了 |

为什么它们都是异步方法？

在整个UI界面下有一个RunLoop事件循环机制，代码的每次操作都基于事件循环。当我们调用setNeedsDisplay或setNeedsLayout时，内部实现仅仅是给某个标志位置1并立即返回，在下一次UI更新轮询的时候就会去调用drawRect或layoutSubviews方法更新UI并将标志位置0，所以在本次事件循环中不会立即调用。

layoutSubviews的触发时机

- 手动调用setNeedsLayout

- addSubview
- view.frame = value
- 滚动一个UIScrollView
- 旋转Screen
- 改变一个UIView大小

drawRect的触发时机

- 手动调用setNeedsDisplay

- 在调用sizeToFit后被调用
- 通过设置contentMode属性值为UIViewContentModeRedraw。那么将在每次设置或更改frame的时候自动调用drawRect

**注意：**layoutSubviews和drawRect不会被自身调用，调用源头是Controller，即init一个View后不会触发上面的方法

> refer: https://www.jianshu.com/p/33a28bb14749

## layoutSubViews & drawRects

参考上面

## CALayer & UIView

CALayer和UIView的设计遵从了面向对象单一职责原则：**CALayer负责显示内容的绘制，UIView则是管理。**

在每一个UIView实例当中，都有一个默认的支持图层layer，UIView负责创建并且管理这个图层。实际上 UIView之所以能够显示,就是因为它里面有这个一个层,才具有显示的功能 ，UIView仅仅是对它的一层封装，实现了CALayer的delegate，提供了处理事件交互的具体功能，还有动画底层方法的高级API。可以说CALayer是UIView的内部实现细节。

区别：

- 首先UIView可以响应事件，而CALayer不可以

- 一个 Layer 的 frame 是由它的 anchorPoint、position、bounds和 transform 共同决定的，而一个 View 的 frame 只是简单的返回 Layer的 frame

- UIView主要是对显示内容的管理而 CALayer 主要侧重显示内容的绘制

- 在做 iOS 动画的时候，修改非 RootLayer的属性（譬如位置、背景色等）会默认产生隐式动画，而修改UIView则不会。

> refer: https://juejin.im/post/5ad9992d6fb9a07abb232745

## UDID & UUID

UDID是Unique Device Identifier的缩写，中文意思是设备唯一标识。

iOS后用`UIDevice.current.identifierForVendor`来获取，它对同一个app供应商是相同的。但这个有坑，app被删后就会重新生成。

UUID是Universally Unique Identifier的缩写，中文意思是通用唯一识别码。`UUID()`就可以生成一个不同的UUID。

Tips：利用Keychain保存UDID或者UUID来保证唯一性。（从用户角度上，不推荐此作法）

> refers:
>
>  https://www.jianshu.com/p/1011c872458d
>
>  https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor

## CPU & GPU

CPU和GPU之所以大不相同，是由于其设计目标的不同，它们分别针对了两种不同的应用场景。CPU需要很强的通用性来处理各种不同的数据类型，同时又要逻辑判断又会引入大量的分支跳转和中断的处理。这些都使得CPU的内部结构异常复杂。而GPU面对的则是类型高度统一的、相互无依赖的大规模数据和不需要被打断的纯净的计算环境。

GPU采用了数量众多的计算单元和超长的流水线，但只有非常简单的控制逻辑并省去了Cache。而CPU不仅被Cache占据了大量空间，而且还有有复杂的控制逻辑和诸多优化电路，相比之下计算能力只是CPU很小的一部分。

CPU 基于低延时的设计；GPU是基于大的吞吐量设计。

**什么类型的程序适合在GPU上运行？**

　　（1）计算密集型的程序。所谓计算密集型(Compute-intensive)的程序，就是其大部分运行时间花在了寄存器运算上，寄存器的速度和处理器的速度相当，从寄存器读写数据几乎没有延时。可以做一下对比，读内存的延迟大概是几百个时钟周期；读硬盘的速度就不说了，即便是SSD, 也实在是太慢了。

　　（2）易于并行的程序。GPU其实是一种SIMD(Single Instruction Multiple Data)架构， 他有成百上千个核，每一个核在同一时间最好能做同样的事情。

> refer: https://www.zhihu.com/question/19903344/answer/96081382
>
> 原文截取自知乎，详细内容请参考上面的链接

## 16、点（pt）& 像素（px）

## 属性与成员变量

成员变量：属于类的内存布局的一部分，在new对象的时候会被创建。

属性：用语法糖包装了一个方法调用，对某一个成员变量的访问，或者成员变量的成员变量或属性的访问。

```objective-c
@interface Label: NSObject {
    @private int _cnt; // 纯粹的成员变量
}
@property(nonatomic, copy) NSString *content; // 编译器会帮助生成一个名叫_content的NSString变量
@property(nonatomic) int cnt; // 自己实现了cnt的get-set方法后，编译器就不会自动生成变量了。
@end
    
@implementation Label
- (int)cnt {
    return _cnt;
}

- (void)setCnt:(int)val {
    _cnt = val;
}
@end
```



## 18、int和NSInteger的区别

（1）import和include

（2）@class

（3）全局 & 静态变量

## 19、类和对象

（1）分类拓展协议中哪些可以声明属性?

（2）继承和类别的区别

（3）分类的作用

（4）分类的局限性

## category & extension

[C]：category为类添加新的方法，甚至属性（关联对象），category可以有多个，每个category都可以遵从一个新的协议；extension又被称作匿名分类，一个类只允许有一个extension，extension中可以添加成员变量、属性、方法等，起到数据和接口隐藏的作用。

Swift中category称作extension，extension的作用和[C]的category功能一致，且没有匿名分类。

**注意：**分类中如果写了已经存在的方法，就会涉及到一个方法覆盖的问题。这个行为是不确定的，具体请参考runtime的消息转发。

## 21、Foundation

（1）字符串

（2）字符串截取

（3）格式

## 22、NSArray和NSDictionary

（1）iOS遍历数组/字典的方法

（2）NSValue NSNumber

（3）其它

（4）如何避免循环引用

## 23、CFSocket使用有哪几个步骤

## 24、Core Foundation中提供了哪几种操作Socket的方法？

## 25、解析XML文件有哪几种方式？

## 26、什么是沙盒模型？哪些操作是属于私有api范畴?

## 在一个对象的方法里面：self.name= “object”；和 name =”object” 有什么不同吗?

点(.)调用的是属性，也就是方法，可以触发KVO。

name = "object"，实际上是直接访问成员变量，即self->name = "object"。

## 29、创建控制器、视图的方式

## 30、简述内存分区情况

## 31、队列和栈有什么区别

## 32、iOS的系统架构

## 33、控件主要响应3种事件

## 34、xib文件的构成分为哪3个图标？都具有什么功能

## 35、简述视图控件器的生命周期

## 36、app 项目的生命周期

（1）应用的生命周期

（2）简要说明一下APP的启动过程，main文件说起，main函数中有什么函数？作用是什么？

（3）UIApplicationMain函数作用

（4）main函数作用

## 37、 动画有基本类型有哪几种；表视图有哪几种基本样式。

## 38、实现简单的表格显示需要设置UITableView的什么属性、实现什么协议？

## 39、Cocoa Touch提供了哪几种Core Animation过渡类型？

## 40、UIView与CLayer有什么区别？

## 41、Quatrz 2D的绘图功能的三个核心概念是什么并简述其作用

## 42、iPhone OS主要提供了几种播放音频的方法？

## 43、使用AVAudioPlayer类调用哪个框架、使用步骤？

## 44、有哪几种手势通知方法、写清楚方法名？

## 45、ViewController的didReceiveMemoryWarning怎么被调用

## 什么时候用delegate,什么时候用Notification?

**delegate**针对**one**-**to-one**关系，并且**reciever**可以返回值给**sender**。

**notification**可以针对**one**-**to**-**one**/**many**/**none**，**reciever**无法返回值给**sender**。

所以**，delegate**用于**sender**希望接受到**reciever**的某个功能反馈值**，notification**用于通知多个**object**某个事件。

> refer: http://www.voidcn.com/article/p-kvhkgpmh-py.html

Thinking：

- delegate需要注意什么？
- 注册了通知需要删除通知吗，如果需要什么时机删除合适？

还有一个使用场景。页面层级跨越很大，此时不适合delegate一层一层传递，用通知会很好地解耦。

## 用预处理指令#define声明一个常数，用以表明1年中有多少秒（忽略闰年问题）

```objective-c
#ifndef ONE_YEAR_SECONDS // 防止重复声明
#define	ONE_YEAR_SECONDS (365 * 24 * 60 * 60) // 表达式需要加上括号，这是陷阱
// 或者
#define ONE_YEAR_SECONDS 31536000 // 直接算出来，常数不用加括号
#endif
```



## 写一个”标准"宏MIN ，这个宏输入两个参数并返回较小的一个

```objective-c
#ifndef MIN
#define MIN(a, b) ((a) > (b) ? (b) : (a)) // 老生常谈，括号，括号
#endif
```



## 关键字const有什么含意？修饰类呢?static的作用,用于类呢?还有extern c的作用

> 有些问的貌似是关于C++的，有的不明所以，这里我就以C++的视角解读一下吧。

### const

const常量修饰关键字，例如：`const int val = 1;`声明一个int的常量。在语义层面上，后续是不可对val进行修改的，否则会被编译器报错。在编译器层面上，会对const修饰的变量优化，即常量传递，在使用val的地方会直接使用数字1，而不是从寄存器中读取val的值。

```c++
#include <iostream>
using namespace  std;
void main()
{
    const int nConst = 5;

    int * pConst = (int*)&nConst;
    *pConst = 6;

    int nVar = nConst;
    cout << "nConst: " << nConst << "  nVar: " << nVar << endl;
}
// 输出：nConst: 5  nVar: 5
// 这段代码，C也是一样
```

区别`const int *obj`和`int *const obj;`

前者obj指向的内容不可更改；后者obj存储的地址不可再改变，指向的内容可以改变。例如：

```objective-c
const int *obj = p;
*obj = 45; // ❌

NSString *const obj2 = @"123";
obj2 = @"1"; // ❌
```

所以，我们经常把这两个结合起来定义[C]对象的常量：`const NSString *const ulr = @"a url"`

在C++中，const还可以被用于成员方法中，表示这个方法中的不会对类的成员变量进行修改。

### static

1. 被static修饰的变量会存储在静态存储区，在程序初始化的时候就会被初始化为对应类型的**零值**。如果是在方法内部的的static变量，只有在第一次执行这个方法的时候才会被初始化，比如创建单例的时候使用:

   ```objective-c
   void singleton() {
       static dispatch_once_t onceToken;
       dispatch_once(&onceToken, ^{
           <#code to be executed once#>
       });
   }
   ```

2. static全局变量，编译器为每一个编译单元生成带有编译单元前缀的符号信息，以保证不同的编译单元不共享同一个static变量。如果某一个头文件含有一个static变量，那么在不同的.m、.mm、.c、.cpp文件中若包含了此头文件，每一个static变量都会是独立的。<sup><a href="static的作用">[1]</a></sup>

> <a name="static的作用">[1]</a> [static的作用](https://www.cnblogs.com/dc10101/archive/2007/08/22/865556.html)

## 50、关键字volatile有什么含意?并给出三个不同的例子

## 51、一个参数既可以是const还可以是volatile吗？ 一个指针可以是volatile 吗？解释为什么。

## 52、static 关键字的作用

## 53、列举几种进程的同步机制，并比较其优缺点。

## 54、进程之间通信的途径

## 55、进程死锁的原因

## 56、死锁的4个必要条件

## 57、死锁的处理

## 58、cocoa touch框架

## 59、自动释放池是什么,如何工作

## 60、sprintf,strcpy,memcpy使用上有什么要注意的地方

## 61、你了解svn,cvs等版本控制工具么？

## 62、什么是push

## 63、静态链接库

## 64、OC三大特性

（1）封装_点语法

（2）继承

（3）多态

## 65、OC中如何实现多态

## 66、Objective-C的优缺点

## 67、对于OC,你认为最大的优点和最大的不足是什么？对于不足之处，现在有没有可用的方法绕过这些不足来实现需求。如果可以话，有没有考虑或者实现过重新实现OC的功能，如果有，具体怎么做？

## 68、oc中可修改和不可以修改类型

## 69、我们说的oc是动态运行时语言是什么意思?

## 70、通知和协议的不同之处?

## 71、什么是推送消息?

## 72、关于多态性

## 73、什么是谓词?

## 74、做过的项目是否涉及网络访问功能，使用什么对象完成网络功能?

## 75、简单介绍下NSURLConnection类及+sendSynchronousRequest:returningResponse:error:与– initWithRequest:delegate:两个方法的区别?

## 76、谈谈Object-C的内存管理方式及过程？

## 77、Object-C有私有方法吗？私有变量呢？

## 78、说说响应链

## 79、时间传递 & 响应者链

## 80、frame和bounds有什么不同?

## 81、方法和选择器有何不同?

## 82、OC的垃圾回收机制?

## 83、什么是延迟加载?

## 84、是否在一个视图控制器中嵌入两个tableview控制器?

## 85、一个tableView是否可以关联两个不同的数据源?你会怎么处理?

## 86、什么时候使用NSMutableArray，什么时候使用NSArray?

## 87、给出委托方法的实例，并且说出UITableVIew的Data Source方法

## 88、在应用中可以创建多少autorelease对象，是否有限制?

## 89、如果我们不创建内存池，是否有内存池提供给我们?

## 90、什么时候需要在程序中创建内存池?

## 91、类NSObject的那些方法经常被使用?

## 92、什么是简便构造方法?

## 93、如何使用Xcode设计通用应用?

## 94、 UIView的动画效果有那些?

## 95、Object-C有多继承吗？没有的话用什么代替？cocoa 中所有的类都是NSObject 的子类

## 96、内存管理 Autorelease、retain、copy、assign的set方法和含义？

## 97、C和obj-c 如何混用

## 98、类别的作用?继承和类别在实现中有何区别?

## 99、类别和类扩展的区别。

## 100、oc中的协议和java中的接口概念有何不同?

## 101、深拷贝与前拷贝区别

（1）什么是深拷贝浅拷贝

（2）字符串什么时候使用copy,strong

（3）字符串所在内存区域

（4）mutablecopy和copy @property(copy) NSMutableArray *arr;这样写有什么问题

（5）如何让自定义类可以使用copy修饰符

## 102、对于语句NSString*obj = [[NSData alloc] init]; obj在编译时和运行时分别时什么类型的对象？

## 103、#import 跟#include 又什么区别，@class呢, ＃import<> 跟 #import”"又什么区别？

## 104、Objective-C的类可以多重继承么?可以实现多个接口么?Category是什么?重写一个类的方法用继承好还是分类好?为什么?

## 105、 #import 跟#include 又什么区别，@class呢, #import<> 跟 #import””又什么区别?

## 106、写一个setter方法用于完成@property (nonatomic,retain)NSString *name,写一个setter方法用于完成@property(nonatomic，copy)NSString *name

## 107、常见的Objective-C的数据类型有那些， 和C的基本数据类型有什么区别?如：NSInteger和int

## 108、id 声明的对象有什么特性?

## 109、Objective-C如何对内存管理的,说说你的看法和解决方法?

## 110、原子(atomic)跟非原子(non-atomic)属性有什么区别?

## 111、看下面的程序,第一个NSLog会输出什么?这时str的retainCount是多少?第二个和第三个呢? 为什么?

## 112、内存管理的几条原则时什么?按照默认法则.那些关键字生成的对象需要手动释放?在和property结合的时候怎样有效的避免内存泄露?

## 113、如何对iOS设备进行性能测试?

## 114、设计模式

（1）mvc模式

（2）单例模式

（3）mvvm模式

（4）观察者模式

（5）工厂模式

（6）代理模式

（7）策略模式

（8）适配器模式

（9）模版模式

（10）外观模式

（11）创建模式

（12）MVP模式

## 115、MVVM模式原理分析

## 116、说说常用的几种传值方式

## 117、什么时候用delegate，什么时候用Notification

## 118、对于单例的理解

## 119、从设计模式角度分析代理，通知和KVO区别？ios SDK 提供 的framework使用了哪些设计模式，为什么使用？有哪些好处和坏处?

## 120、KVO，NSNotification，delegate及block区别

## 121、运行时（runTime）

## 122、runtime/消息转发机制

（1）runtime

1.1、什么是runtime

1.2、runtime干什么用，使用场景

（2）消息机制

2.1、消息转发的原理

2.2、SEL isa super cmd 是什么

（3）动态绑定

## 123、使用bugly进行崩溃分析

## 124、jenkens 持续打包

## 125、KVO & KVC

（1）底层实现

（2）KVO概述

（3）KVC概述

## 126、什么是KVO和KVC?

KVO和KVC

（1）如何调用私有变量，如何修改系统的只读属性，KVC的查找顺序

（2）什么是键-值,键路径是什么

（3）kvo的实现机制

（4）KVO计算属性，设置依赖键

（5）KVO集合属性

（6）kvo使用场景

## 127、SDWebImage(SDWebImage的实现机制）

（1）主要功能

（2）缓存

（3）内存缓存与磁盘缓存

## 128、框架 SDWebimage的缓存机制

## 129、网络安全

密码的安全原则

## 130、多线程

（1）多线程概念

（2）多线程的作用

（3）使用场景

## 131、NSOperationQueue和GCD的区别是什么

## 132、GCD与NSThread的区别

## 133、进程和线程的区别与联系是什么?

## 134、别异步执行两个耗时操作，等两次耗时操作都执行完毕后,再回到主线程执行操作. 使用队列组(dispatch_group_t)快速,高效的实现上述需求

## 135、在项目什么时候选择使用GCD，什么时候选择NSOperation?

## 136、对比iOS中的多线程技术

## 137、多线程优缺点

## 138、iOS中的延迟操作

## 139、串行队列同步执行和异步主队列

## 140、资源抢夺解决方案

## 141、dispatch_barrier_async的作用是什么？

## 142、在多线程Core Data中，NSC,MOC,NSObjectModel哪些需要在线程中创建或者传递？你是用什么策越来实现的？

## 143、+(void)load与 +(void)initialize区别load 和 initialize方法的区别

## 144、http的post与区别与联系，实践中如何选择它们？

## 145、说说关于UDP/TCP的区别？

## 146、http和scoket通信的区别?socket连接相关库,TCP,UDP的连接方法,HTTP的几种常用方式?

## 147、HTTP请求常用的几种方式

## 148、block

（1）使用block时什么情况会发生引用循环，如何解决？

（2）在block内如何修改block外部变量？

（3）Block & MRC-Block

（4）什么是block

（5）block 实现原理

（6）关于block

（7）使用block和使用delegate完成委托模式有什么优点

（8）多线程与block

（9）谈谈对Block 的理解?并写出一个使用Block执行UIVew动画?

（10）写出上面代码的Block的定义（接上题）

## 149、Weak、strong、copy、assign 使用

（1）什么情况使用 weak 关键字，相比 assign 有什么不同？

（2）怎么用 copy 关键字？

（3）weak & strong

（4）这个写法会出什么问题： @property (copy) NSMutableArray *array

（5） 如何让自己的类用 copy 修饰符？如何重写带 copy 关键字的 setter？

（6） @property 的本质是什么？ivar、getter、setter 是如何生成并添加到这个类中的

（7）ivar、getter、setter 是如何生成并添加到这个类中的?

（8）用@property声明的NSString（或NSArray，NSDictionary）经常使用copy关键字，为什么？如果改用strong关键字，可能造成什么问题？

（9）@protocol 和 category 中如何使用 @property

（10）runtime如何通过selector找到对应的IMP地址？

（11）retain和copy区别

（12）copy和strong的使用？

（13）NSString和NSMutableString，前者线程安全，后者线程不安全。

（14）readwrite，readonly，assign，retain，copy，weak ,strong,nonatomic 属性的作用

## 150、OC与JS的交互（iOS与H5混编）

TableView性能优化

UITableView核心思想

UITableView的优化主要从三个方面入手：

## 151、TableView为什么会卡？

## 152、UITableView

（1）UITableView最核心的思想

（2）定义高度

（3）自定义高度原理

（4）老生常谈之UITableView的性能优化

（5）cell高度的计算

（5.1）定高的cell和动态高度的cell

（6）TableView渲染

（7）减少视图的数目

（8）减少多余的绘制操作

（9）不要给cell动态添加subView

（10）异步化UI，不要阻塞主线程

（11）滑动时按需加载对应的内容

（12）离屏渲染的问题

（13）离屏渲染优化方案

## 153、环信SDK使用

这个没使用过

## 154、蓝牙

## 155、在iPhone应用中如何保存数据?

## 156、什么是coredata?

## 157、 什么是NSManagedObject模型?

## 158、什么是NSManagedobjectContext?

## 159、 iOS平台怎么做数据的持久化?coredata 和sqlite有无必然联系？coredata是一个关系型数据库吗？

## 160、CoreData & SQLite3

## 161、数据存储

（1）数据存储技术

（1.1）数据存储的几种方式

（1.2）各自特点（面试考点）

（1.3）偏好设置（面试考点）

（1.4）归档（面试考点）

（2）数据库技术（SQLite&CoreData）

## 162、Objective-C堆和栈的区别？

## 163、内存泄露 & 内存溢出

## 164、堆 & 栈

（1）堆栈空间分配区别

（2）堆栈缓存方式区别

（3）堆栈数据结构区别

## 165、内存管理

（1）内存区域

（1.1）堆和栈的区别

（1.2）iOS内存区域

（2）字符串的内存管理

（3）你是如何优化内存管理

（4）循环引用

（5）autorelease的使用

（5.1）工厂方法为什么不释放对象

（5.2）ARC下autorelease的使用场景

（5.3）自动释放池如何工作

（5.4）避免内存峰值

（5.5）ARC和MRC的混用

（5.6）NSTimer的内存管理

（5.7）ARC的实现原理

## 166、Runloop

## 167、fmmpeg框架

## 168、fmdb框架

## 169、320框架

## 170、UIKit和CoreAnimation和CoreGraphics的关系是什么？在开发中是否使用过CoreAnimation和CoreGraphics?

## 171、trasform

## 172、点讲动画和layer ,view的区别

## 173、图层与视图

## 174、平行的层级关系

## 175、图层的能力

## 176、使用图层

## 177、核心绘图

（1）View和layer的区别

（2）new和alloc init的区别

## 178、动画

## 179、UICollectionView

（1）何实现瀑布流,流水布局

（2）和UITableView的使用区别

## 180、UIImage

## 181、webview

## 182、描述九宫格算法

## 183、实现图片轮播图

## 184、iOS网络框架

## 185、网络

（1）网络基础

（2）网络传输

（3）AFN

## 186、AFNetworking & ASIHttpRequest & MKNetWorking

（1）底层实现

（2）对服务器返回的数据处理

（3）监听请求过程

（4）在文件下载和文件上传的使用难易度

（5）网络监控

（6）ASI提供的其他实用功能

（7）MKNetworkKit

## 187、性能优化

## 188、算法

客户端使用到的算法不多，true或false的存储比较多一点，比如某个设置是否开启啊，这儿可以用bit来优化。（纯属抛砖引玉）