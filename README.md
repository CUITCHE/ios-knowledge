# ios-knowledge

Some summaries of iOS knowledge points

<!-- TOC -->autoauto- [ios-knowledge](#ios-knowledge)auto    - [Swift和[C]的区别](#swift和c的区别)auto    - [2、编译链接](#2编译链接)auto    - [3、synthesize & dynamic](#3synthesize--dynamic)auto    - [在项目开发中常用的开发工具有哪些？](#在项目开发中常用的开发工具有哪些)auto    - [5、UITableView & UICollection](#5uitableview--uicollection)auto    - [6、NSProxy & NSObject](#6nsproxy--nsobject)auto    - [7、Object & Swift](#7object--swift)auto    - [8、传值通知 & 推送通知（本地&远程）](#8传值通知--推送通知本地远程)auto    - [9、第三方库 & 第三方平台](#9第三方库--第三方平台)auto    - [10、NSCache & NSDcitionary](#10nscache--nsdcitionary)auto    - [11、 UIView的setNeedsDisplay和setNeedsLayout方法](#11-uiview的setneedsdisplay和setneedslayout方法)auto    - [12、UILayer & UIView](#12uilayer--uiview)auto    - [13、layoutSubViews & drawRects](#13layoutsubviews--drawrects)auto    - [14、UDID & UUID](#14udid--uuid)auto    - [15、CPU & GPU](#15cpu--gpu)auto    - [16、点（pt）& 像素（px）](#16点pt-像素px)auto    - [17、属性与成员变量](#17属性与成员变量)auto    - [18、int和NSInteger的区别](#18int和nsinteger的区别)auto    - [19、类和对象](#19类和对象)auto    - [20、category & extension](#20category--extension)auto    - [21、Foundation](#21foundation)auto    - [22、NSArray和NSDictionary](#22nsarray和nsdictionary)auto    - [23、CFSocket使用有哪几个步骤](#23cfsocket使用有哪几个步骤)auto    - [24、Core Foundation中提供了哪几种操作Socket的方法？](#24core-foundation中提供了哪几种操作socket的方法)auto    - [25、解析XML文件有哪几种方式？](#25解析xml文件有哪几种方式)auto    - [26、什么是沙盒模型？哪些操作是属于私有api范畴?](#26什么是沙盒模型哪些操作是属于私有api范畴)auto    - [27、在一个对象的方法里面：self.name= “object”；和 name =”object” 有什么不同吗?](#27在一个对象的方法里面selfname-object和-name-object-有什么不同吗)auto    - [28、请简要说明viewDidLoad和viewDidUnload何时调用](#28请简要说明viewdidload和viewdidunload何时调用)auto    - [29、创建控制器、视图的方式](#29创建控制器视图的方式)auto    - [30、简述内存分区情况](#30简述内存分区情况)auto    - [31、队列和栈有什么区别](#31队列和栈有什么区别)auto    - [32、iOS的系统架构](#32ios的系统架构)auto    - [33、控件主要响应3种事件](#33控件主要响应3种事件)auto    - [34、xib文件的构成分为哪3个图标？都具有什么功能](#34xib文件的构成分为哪3个图标都具有什么功能)auto    - [35、简述视图控件器的生命周期](#35简述视图控件器的生命周期)auto    - [36、app 项目的生命周期](#36app-项目的生命周期)auto    - [37、 动画有基本类型有哪几种；表视图有哪几种基本样式。](#37-动画有基本类型有哪几种表视图有哪几种基本样式)auto    - [38、实现简单的表格显示需要设置UITableView的什么属性、实现什么协议？](#38实现简单的表格显示需要设置uitableview的什么属性实现什么协议)auto    - [39、Cocoa Touch提供了哪几种Core Animation过渡类型？](#39cocoa-touch提供了哪几种core-animation过渡类型)auto    - [40、UIView与CLayer有什么区别？](#40uiview与clayer有什么区别)auto    - [41、Quatrz 2D的绘图功能的三个核心概念是什么并简述其作用](#41quatrz-2d的绘图功能的三个核心概念是什么并简述其作用)auto    - [42、iPhone OS主要提供了几种播放音频的方法？](#42iphone-os主要提供了几种播放音频的方法)auto    - [43、使用AVAudioPlayer类调用哪个框架、使用步骤？](#43使用avaudioplayer类调用哪个框架使用步骤)auto    - [44、有哪几种手势通知方法、写清楚方法名？](#44有哪几种手势通知方法写清楚方法名)auto    - [45、ViewController的didReceiveMemoryWarning怎么被调用](#45viewcontroller的didreceivememorywarning怎么被调用)auto    - [46、什么时候用delegate,什么时候用Notification?](#46什么时候用delegate什么时候用notification)auto    - [47、用预处理指令#define声明一个常数，用以表明1年中有多少秒（忽略闰年问题）](#47用预处理指令define声明一个常数用以表明1年中有多少秒忽略闰年问题)auto    - [48、写一个”标准"宏MIN ，这个宏输入两个参数并返回较小的一个。](#48写一个标准宏min-这个宏输入两个参数并返回较小的一个)auto    - [49、关键字const有什么含意？修饰类呢?static的作用,用于类呢?还有extern c的作用](#49关键字const有什么含意修饰类呢static的作用用于类呢还有extern-c的作用)auto    - [50、关键字volatile有什么含意?并给出三个不同的例子](#50关键字volatile有什么含意并给出三个不同的例子)auto    - [51、一个参数既可以是const还可以是volatile吗？ 一个指针可以是volatile 吗？解释为什么。](#51一个参数既可以是const还可以是volatile吗-一个指针可以是volatile-吗解释为什么)auto    - [52、static 关键字的作用](#52static-关键字的作用)auto    - [53、列举几种进程的同步机制，并比较其优缺点。](#53列举几种进程的同步机制并比较其优缺点)auto    - [54、进程之间通信的途径](#54进程之间通信的途径)auto    - [55、进程死锁的原因](#55进程死锁的原因)auto    - [56、死锁的4个必要条件](#56死锁的4个必要条件)auto    - [57、死锁的处理](#57死锁的处理)auto    - [58、cocoa touch框架](#58cocoa-touch框架)auto    - [59、自动释放池是什么,如何工作](#59自动释放池是什么如何工作)auto    - [60、sprintf,strcpy,memcpy使用上有什么要注意的地方](#60sprintfstrcpymemcpy使用上有什么要注意的地方)auto    - [61、你了解svn,cvs等版本控制工具么？](#61你了解svncvs等版本控制工具么)auto    - [62、什么是push](#62什么是push)auto    - [63、静态链接库](#63静态链接库)auto    - [64、OC三大特性](#64oc三大特性)auto    - [65、OC中如何实现多态](#65oc中如何实现多态)auto    - [66、Objective-C的优缺点](#66objective-c的优缺点)auto    - [67、对于OC,你认为最大的优点和最大的不足是什么？对于不足之处，现在有没有可用的方法绕过这些不足来实现需求。如果可以话，有没有考虑或者实现过重新实现OC的功能，如果有，具体怎么做？](#67对于oc你认为最大的优点和最大的不足是什么对于不足之处现在有没有可用的方法绕过这些不足来实现需求如果可以话有没有考虑或者实现过重新实现oc的功能如果有具体怎么做)auto    - [68、oc中可修改和不可以修改类型](#68oc中可修改和不可以修改类型)auto    - [69、我们说的oc是动态运行时语言是什么意思?](#69我们说的oc是动态运行时语言是什么意思)auto    - [70、通知和协议的不同之处?](#70通知和协议的不同之处)auto    - [71、什么是推送消息?](#71什么是推送消息)auto    - [72、关于多态性](#72关于多态性)auto    - [73、什么是谓词?](#73什么是谓词)auto    - [74、做过的项目是否涉及网络访问功能，使用什么对象完成网络功能?](#74做过的项目是否涉及网络访问功能使用什么对象完成网络功能)auto    - [75、简单介绍下NSURLConnection类及+sendSynchronousRequest:returningResponse:error:与– initWithRequest:delegate:两个方法的区别?](#75简单介绍下nsurlconnection类及sendsynchronousrequestreturningresponseerror与-initwithrequestdelegate两个方法的区别)auto    - [76、谈谈Object-C的内存管理方式及过程？](#76谈谈object-c的内存管理方式及过程)auto    - [77、Object-C有私有方法吗？私有变量呢？](#77object-c有私有方法吗私有变量呢)auto    - [78、说说响应链](#78说说响应链)auto    - [79、时间传递 & 响应者链](#79时间传递--响应者链)auto    - [80、frame和bounds有什么不同?](#80frame和bounds有什么不同)auto    - [81、方法和选择器有何不同?](#81方法和选择器有何不同)auto    - [82、OC的垃圾回收机制?](#82oc的垃圾回收机制)auto    - [83、什么是延迟加载?](#83什么是延迟加载)auto    - [84、是否在一个视图控制器中嵌入两个tableview控制器?](#84是否在一个视图控制器中嵌入两个tableview控制器)auto    - [85、一个tableView是否可以关联两个不同的数据源?你会怎么处理?](#85一个tableview是否可以关联两个不同的数据源你会怎么处理)auto    - [86、什么时候使用NSMutableArray，什么时候使用NSArray?](#86什么时候使用nsmutablearray什么时候使用nsarray)auto    - [87、给出委托方法的实例，并且说出UITableVIew的Data Source方法](#87给出委托方法的实例并且说出uitableview的data-source方法)auto    - [88、在应用中可以创建多少autorelease对象，是否有限制?](#88在应用中可以创建多少autorelease对象是否有限制)auto    - [89、如果我们不创建内存池，是否有内存池提供给我们?](#89如果我们不创建内存池是否有内存池提供给我们)auto    - [90、什么时候需要在程序中创建内存池?](#90什么时候需要在程序中创建内存池)auto    - [91、类NSObject的那些方法经常被使用?](#91类nsobject的那些方法经常被使用)auto    - [92、什么是简便构造方法?](#92什么是简便构造方法)auto    - [93、如何使用Xcode设计通用应用?](#93如何使用xcode设计通用应用)auto    - [94、 UIView的动画效果有那些?](#94-uiview的动画效果有那些)auto    - [95、Object-C有多继承吗？没有的话用什么代替？cocoa 中所有的类都是NSObject 的子类](#95object-c有多继承吗没有的话用什么代替cocoa-中所有的类都是nsobject-的子类)auto    - [96、内存管理 Autorelease、retain、copy、assign的set方法和含义？](#96内存管理-autoreleaseretaincopyassign的set方法和含义)auto    - [97、C和obj-c 如何混用](#97c和obj-c-如何混用)auto    - [98、类别的作用?继承和类别在实现中有何区别?](#98类别的作用继承和类别在实现中有何区别)auto    - [99、类别和类扩展的区别。](#99类别和类扩展的区别)auto    - [100、oc中的协议和java中的接口概念有何不同?](#100oc中的协议和java中的接口概念有何不同)auto    - [101、深拷贝与前拷贝区别](#101深拷贝与前拷贝区别)auto    - [102、对于语句NSString*obj = [[NSData alloc] init]; obj在编译时和运行时分别时什么类型的对象？](#102对于语句nsstringobj--nsdata-alloc-init-obj在编译时和运行时分别时什么类型的对象)auto    - [103、#import 跟#include 又什么区别，@class呢, ＃import<> 跟 #import”"又什么区别？](#103import-跟include-又什么区别class呢-＃import-跟-import又什么区别)auto    - [104、Objective-C的类可以多重继承么?可以实现多个接口么?Category是什么?重写一个类的方法用继承好还是分类好?为什么?](#104objective-c的类可以多重继承么可以实现多个接口么category是什么重写一个类的方法用继承好还是分类好为什么)auto    - [105、 #import 跟#include 又什么区别，@class呢, #import<> 跟 #import””又什么区别?](#105-import-跟include-又什么区别class呢-import-跟-import又什么区别)auto    - [106、写一个setter方法用于完成@property (nonatomic,retain)NSString *name,写一个setter方法用于完成@property(nonatomic，copy)NSString *name](#106写一个setter方法用于完成property-nonatomicretainnsstring-name写一个setter方法用于完成propertynonatomiccopynsstring-name)auto    - [107、常见的Objective-C的数据类型有那些， 和C的基本数据类型有什么区别?如：NSInteger和int](#107常见的objective-c的数据类型有那些-和c的基本数据类型有什么区别如nsinteger和int)auto    - [108、id 声明的对象有什么特性?](#108id-声明的对象有什么特性)auto    - [109、Objective-C如何对内存管理的,说说你的看法和解决方法?](#109objective-c如何对内存管理的说说你的看法和解决方法)auto    - [110、原子(atomic)跟非原子(non-atomic)属性有什么区别?](#110原子atomic跟非原子non-atomic属性有什么区别)auto    - [111、看下面的程序,第一个NSLog会输出什么?这时str的retainCount是多少?第二个和第三个呢? 为什么?](#111看下面的程序第一个nslog会输出什么这时str的retaincount是多少第二个和第三个呢-为什么)auto    - [112、内存管理的几条原则时什么?按照默认法则.那些关键字生成的对象需要手动释放?在和property结合的时候怎样有效的避免内存泄露?](#112内存管理的几条原则时什么按照默认法则那些关键字生成的对象需要手动释放在和property结合的时候怎样有效的避免内存泄露)auto    - [113、如何对iOS设备进行性能测试?](#113如何对ios设备进行性能测试)auto    - [114、设计模式](#114设计模式)auto    - [115、MVVM模式原理分析](#115mvvm模式原理分析)auto    - [116、说说常用的几种传值方式](#116说说常用的几种传值方式)auto    - [117、什么时候用delegate，什么时候用Notification](#117什么时候用delegate什么时候用notification)auto    - [118、对于单例的理解](#118对于单例的理解)auto    - [119、从设计模式角度分析代理，通知和KVO区别？ios SDK 提供 的framework使用了哪些设计模式，为什么使用？有哪些好处和坏处?](#119从设计模式角度分析代理通知和kvo区别ios-sdk-提供-的framework使用了哪些设计模式为什么使用有哪些好处和坏处)auto    - [120、KVO，NSNotification，delegate及block区别](#120kvonsnotificationdelegate及block区别)auto    - [121、运行时（runTime）](#121运行时runtime)auto    - [122、runtime/消息转发机制](#122runtime消息转发机制)auto    - [123、使用bugly进行崩溃分析](#123使用bugly进行崩溃分析)auto    - [124、jenkens 持续打包](#124jenkens-持续打包)auto    - [125、KVO & KVC](#125kvo--kvc)auto    - [126、什么是KVO和KVC?](#126什么是kvo和kvc)auto    - [127、SDWebImage(SDWebImage的实现机制）](#127sdwebimagesdwebimage的实现机制)auto    - [128、框架 SDWebimage的缓存机制](#128框架-sdwebimage的缓存机制)auto    - [129、网络安全](#129网络安全)auto    - [130、多线程](#130多线程)auto    - [131、NSOperationQueue和GCD的区别是什么](#131nsoperationqueue和gcd的区别是什么)auto    - [132、GCD与NSThread的区别](#132gcd与nsthread的区别)auto    - [133、进程和线程的区别与联系是什么?](#133进程和线程的区别与联系是什么)auto    - [134、别异步执行两个耗时操作，等两次耗时操作都执行完毕后,再回到主线程执行操作. 使用队列组(dispatch_group_t)快速,高效的实现上述需求](#134别异步执行两个耗时操作等两次耗时操作都执行完毕后再回到主线程执行操作-使用队列组dispatch_group_t快速高效的实现上述需求)auto    - [135、在项目什么时候选择使用GCD，什么时候选择NSOperation?](#135在项目什么时候选择使用gcd什么时候选择nsoperation)auto    - [136、对比iOS中的多线程技术](#136对比ios中的多线程技术)auto    - [137、多线程优缺点](#137多线程优缺点)auto    - [138、iOS中的延迟操作](#138ios中的延迟操作)auto    - [139、串行队列同步执行和异步主队列](#139串行队列同步执行和异步主队列)auto    - [140、资源抢夺解决方案](#140资源抢夺解决方案)auto    - [141、dispatch_barrier_async的作用是什么？](#141dispatch_barrier_async的作用是什么)auto    - [142、在多线程Core Data中，NSC,MOC,NSObjectModel哪些需要在线程中创建或者传递？你是用什么策越来实现的？](#142在多线程core-data中nscmocnsobjectmodel哪些需要在线程中创建或者传递你是用什么策越来实现的)auto    - [143、+(void)load与 +(void)initialize区别load 和 initialize方法的区别](#143voidload与-voidinitialize区别load-和-initialize方法的区别)auto    - [144、http的post与区别与联系，实践中如何选择它们？](#144http的post与区别与联系实践中如何选择它们)auto    - [145、说说关于UDP/TCP的区别？](#145说说关于udptcp的区别)auto    - [146、http和scoket通信的区别?socket连接相关库,TCP,UDP的连接方法,HTTP的几种常用方式?](#146http和scoket通信的区别socket连接相关库tcpudp的连接方法http的几种常用方式)auto    - [147、HTTP请求常用的几种方式](#147http请求常用的几种方式)auto    - [148、block](#148block)auto    - [149、Weak、strong、copy、assign 使用](#149weakstrongcopyassign-使用)auto    - [150、OC与JS的交互（iOS与H5混编）](#150oc与js的交互ios与h5混编)auto    - [151、TableView为什么会卡？](#151tableview为什么会卡)auto    - [152、UITableView](#152uitableview)auto    - [153、环信SDK使用](#153环信sdk使用)auto    - [154、蓝牙](#154蓝牙)auto    - [155、在iPhone应用中如何保存数据?](#155在iphone应用中如何保存数据)auto    - [156、什么是coredata?](#156什么是coredata)auto    - [157、 什么是NSManagedObject模型?](#157-什么是nsmanagedobject模型)auto    - [158、什么是NSManagedobjectContext?](#158什么是nsmanagedobjectcontext)auto    - [159、 iOS平台怎么做数据的持久化?coredata 和sqlite有无必然联系？coredata是一个关系型数据库吗？](#159-ios平台怎么做数据的持久化coredata-和sqlite有无必然联系coredata是一个关系型数据库吗)auto    - [160、CoreData & SQLite3](#160coredata--sqlite3)auto    - [161、数据存储](#161数据存储)auto    - [162、Objective-C堆和栈的区别？](#162objective-c堆和栈的区别)auto    - [163、内存泄露 & 内存溢出](#163内存泄露--内存溢出)auto    - [164、堆 & 栈](#164堆--栈)auto    - [165、内存管理](#165内存管理)auto    - [166、Runloop](#166runloop)auto    - [167、fmmpeg框架](#167fmmpeg框架)auto    - [168、fmdb框架](#168fmdb框架)auto    - [169、320框架](#169320框架)auto    - [170、UIKit和CoreAnimation和CoreGraphics的关系是什么？在开发中是否使用过CoreAnimation和CoreGraphics?](#170uikit和coreanimation和coregraphics的关系是什么在开发中是否使用过coreanimation和coregraphics)auto    - [171、trasform](#171trasform)auto    - [172、点讲动画和layer ,view的区别](#172点讲动画和layer-view的区别)auto    - [173、图层与视图](#173图层与视图)auto    - [174、平行的层级关系](#174平行的层级关系)auto    - [175、图层的能力](#175图层的能力)auto    - [176、使用图层](#176使用图层)auto    - [177、核心绘图](#177核心绘图)auto    - [178、动画](#178动画)auto    - [179、UICollectionView](#179uicollectionview)auto    - [180、UIImage](#180uiimage)auto    - [181、webview](#181webview)auto    - [182、描述九宫格算法](#182描述九宫格算法)auto    - [183、实现图片轮播图](#183实现图片轮播图)auto    - [184、iOS网络框架](#184ios网络框架)auto    - [185、网络](#185网络)auto    - [186、AFNetworking & ASIHttpRequest & MKNetWorking](#186afnetworking--asihttprequest--mknetworking)auto    - [187、性能优化](#187性能优化)auto    - [188、算法](#188算法)autoauto<!-- /TOC -->

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

    ​		此外协议可以被应用于泛型；可以扩展协议，在扩展中自定义方法或给协议中的方法提供默认实现

    ```swift
    protocol Animal {
        func walk()
        var name: String { get set }
    }

    extension Animal {
        func walk() {
            // some code...
        }

        func anotherFunction() {
            // ...
        }
    }
    ```



- 泛型

  - [C] 不支持

  - Swift 一大亮点，更安全的泛型；弱化的契约编程，可以指定泛型的基础类型。

- 结构体、类

  - [C]	<u>结构体</u>就是C语言的东西，属于值类型，由编译器管理生命周期。由于结构体没有析构函数（C++中的结构体如果包含方法就会升级为C++类），所以结构体不能含有[C]对象，因为编译器不知道在什么地方release对象才好。

    ​	<u>类</u>是包含了一个runtime的C的结构体，属于指针类型，采用引用计数管理生命周期。

  - Swift 也有结构体和类的区别。和[C]一样，结构体是值类型，类是指针（引用）类型。但Swift中结构体更强大，除了不能被继承、没有析构函数（deinit）外拥有类的所有功能。

- 类型安全

  - [C]	[C]的对象在编译期都可以被看作id类型，一个方法的参数需要接收类型A，在直接调用的地方也确实传了类型A的对象，但是有时候这个对象来自外部，而外部有可能莫名其妙传了一个类型B进来，编译的时候有可能还通过了，导致在运行时会出现找不到某某方法的selector而崩溃。

  - Swift 强静态类型语言，A就是A，B就是B，不会出现C/C++的隐式转换。

    ```swift
    let a = 1.23 // Double类型
    let b: Int = a // ❌ 无法直接从Double转换成Int，需要通过构造函数 Int(a)才行
    ```



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

## 11、 UIView的setNeedsDisplay和setNeedsLayout方法

## 12、UILayer & UIView

## 13、layoutSubViews & drawRects

## 14、UDID & UUID

## 15、CPU & GPU

## 16、点（pt）& 像素（px）

## 17、属性与成员变量

## 18、int和NSInteger的区别

（1）import和include

（2）@class

（3）全局 & 静态变量

## 19、类和对象

（1）分类拓展协议中哪些可以声明属性?

（2）继承和类别的区别

（3）分类的作用

（4）分类的局限性

## 20、category & extension

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

## 27、在一个对象的方法里面：self.name= “object”；和 name =”object” 有什么不同吗?

## 28、请简要说明viewDidLoad和viewDidUnload何时调用

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

## 46、什么时候用delegate,什么时候用Notification?

## 47、用预处理指令#define声明一个常数，用以表明1年中有多少秒（忽略闰年问题）

## 48、写一个”标准"宏MIN ，这个宏输入两个参数并返回较小的一个。

## 49、关键字const有什么含意？修饰类呢?static的作用,用于类呢?还有extern c的作用

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
