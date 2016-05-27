#Apple Watch开发的几个小问题

20160522

##### Q1 如何在调试AppleWatch的时候对watch程序打断点

1. 在Xcode的Target选择AppleWatch程序

2. Watch应用启动之后再打开iPhone模拟器中的程序,然后回到Xcode,选择菜单里的Debug->Attach to Process by PID or name ,填写apple watch extension 的bundle identifier

断点就可以生效了


##### Q2 WatchKit 架构变化

在 watchOS 1 做过开发的人，都应该熟悉如下这张图：

![](http://7u2mu6.com1.z0.glb.clouddn.com/QQ20151017-4.png)


如上图所示，在 watchOS 1 上面做开发，Apple Watch 应用程序由两部分构成：Watch App 和 WatchKit 扩展。

Watch App 是一个运行在 Apple Watch 中的可执行文件。它包括 storyboard 和渲染屏幕时所需的资源文件。

WatchKit 扩展则是运行在 iPhone 上的可执行文件。包括管理应用程序界面的逻辑代码，以及处理用户的交互操作。

那么，在 watchOS 2 中，WatchKit 的架构发生了比较重大的变化，我们先来看看下面这张图：

![](http://7u2mu6.com1.z0.glb.clouddn.com/QQ20151017-5.png)

从上面的图中，可以很明显地看出，苹果把原来运行在 iPhone 手机上的 WatchKit Extension 移到 Apple Watch 中了。这将直接带来如下改变：原来只存放一些资源和 Storyboard 的 Watch App，现在程序的业务逻辑部分（也就是代码执行部分）也被放到 Watch App 中。这样的话，程序给用户的体验会更好，Watch App 的运行可以完全独立于 iPhone 了。



##### Q3 watch os 1 & watch os 2 获取网络资源的方法

watch os 1主要是通过WKInterfaceController的
<pre>
+ (BOOL)openParentApplication:(NSDictionary *)userInfo reply:(nullable void(^)(NSDictionary * replyInfo, NSError * __nullable error)) reply WK_AVAILABLE_IOS_ONLY(8.2);    // launches containing iOS application on the phone. userInfo must be non-nil

</pre>
方法交给iPhone去处理，当iPhone收到消息后在AppDelegate中收到回调
<pre>
- (void)application:(UIApplication *)application handleWatchKitExtensionRequest:(NSDictionary *)userInfo reply:(void (^)(NSDictionary *))reply
{}
</pre>
到这里后交给NSURLSession或者NSURLConnection处理。

watch os 2基于watch架构变化后，可以直接由watch发起网络请求，值得注意的是，Apple Watch 2 中还支持 WiFi，所以 Apple Watch 可以通过 WiFi，直接获取一些网络数据等。并且 Apple Watch 无法处理的一些业务，可以通过 WatchConnectivity 框架的WCSession，请求 iPhone 进行处理，并将结果返回给 Apple Watch。



##### Q4 Apple Watch强退App的方法

虽然apple watch的应用没有真正意义上的后台，表冠退出应用以后就不在运行（部分自带应用的检测功能不会退出）了，但下一次启动应用会很快。可是作为一名强迫症十分想关闭后台应用，于是发现一种关闭后台应用的方法：如要完全退出健身应用，

第一步：进入健身应用界面

![](http://images.weiphone.net/data/attachment/forum/201505/07/112751r24zbqkjyzq13znl.png)

第二步：按住（长按）侧边按钮，出现关机/省电模式界面后松开按钮。

![](http://images.weiphone.net/data/attachment/forum/201505/07/112826ivzav878k77x3xyh.png) 

第三部：不要管界面内容，再次按住（长按）侧边按钮，大约3秒后应用被完全退出。

如果再一次打开这个应用可能会需要一点加载时间。


##### Q5 wkinterfacecontroller的生命周期

watch app是Page-Based，可以左右滑动，假设有三个interfacecontroller，刚启动的时候，它们大概是下面这样运行

<pre>
2016-05-18 18:58:48.793 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController init]
2016-05-18 18:58:48.793 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController awakeWithContext:]
2016-05-18 18:58:48.793 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController init]
2016-05-18 18:58:48.794 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController awakeWithContext:]
2016-05-18 18:58:48.794 MonkeyForWatch WatchKit Extension[13295:382024] -[SettingInterfaceController init]
2016-05-18 18:58:48.794 MonkeyForWatch WatchKit Extension[13295:382024] -[SettingInterfaceController awakeWithContext:]
2016-05-18 18:58:48.794 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController willActivate]
2016-05-18 18:58:48.794 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController didAppear]
2016-05-18 18:58:49.297 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController willActivate]
2016-05-18 18:58:49.298 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController didDeactivate]

</pre>

由InterfaceController滑动到RepositoryInterfaceController之后

<pre>


2016-05-18 19:01:31.941 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController willDisappear]
2016-05-18 19:01:31.941 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController willActivate]
2016-05-18 19:01:31.942 MonkeyForWatch WatchKit Extension[13295:382024] -[InterfaceController didDeactivate]
2016-05-18 19:01:31.942 MonkeyForWatch WatchKit Extension[13295:382024] -[RepositoryInterfaceController didAppear]
2016-05-18 19:01:32.445 MonkeyForWatch WatchKit Extension[13295:382024] -[SettingInterfaceController willActivate]
2016-05-18 19:01:37.710 MonkeyForWatch WatchKit Extension[13295:382024] -[SettingInterfaceController didDeactivate]


</pre>


##### Q6 WKInterfaceTable如何使用

首先需要storyboard中建立表以及自定义的row，下面是初始化表视图，SettingRow是一个NSObject对象。


<pre>
- (void)initTable
{
    [self.settingTable setNumberOfRows:2 withRowType:NSStringFromClass([SettingRow class])];
    
    for (NSInteger i=0; i<2; i++) {
        SettingRow *elementRow = (SettingRow *)[self.settingTable rowControllerAtIndex:i];
        [elementRow.titleLabel setText:[NSString stringWithFormat:@"%@ 设置开发语言",@(i)]];
    }
}
</pre>

table的点击事件则需要复写WKInterfaceController的方法
<pre>
- (void)table:(WKInterfaceTable *)table didSelectRowAtIndex:(NSInteger)rowIndex;  // row selection if controller has WKInterfaceTable property
{
    if (rowIndex==0) {
        [self presentControllerWithName:NSStringFromClass([LanguageListInterfaceController class]) context:nil];
    }
}
</pre>

##### Q7 三种交互方式

Apple Watch将会有三种交互方式：主屏幕下，佩戴者可以看到所有的Watch app，用户点击后就可以直接启动相应app；第二种交互方式被称做“Glance”，该界面下不含按钮，也不可滑动，用户只能够进行快速阅读，内容将只有一屏空间。开发者可以定制该界面，用户点击后即会启动相应app。第三种交互方式是通知提醒的定制操作。当iPhone上的通知推送至Apple Watch上显示后，当用户点击后就可以进入更详细的信息显示页面，开发者可以对该界面进行定制。

![](http://cdn.pingwest.com/wp-content/uploads/2014/11/WatchKit.jpg?imageView2/2/w/750/q/90)


##### Q8 兼容iOS6的问题

在iOS6的机器上运行，我发现了一下问题，

<pre>
dyld: Library not loaded: /System/Library/Frameworks/WatchKit.framework/WatchKit
Referenced from: /var/mobile/Applications/xxxx/xxx.app/xxx
Reason: image not found
(lldb) 
</pre>

因为watchkit.framework 在iOS 6上是不存在的，所以才会有上面的错误，这时需要在build phases里把watchkit.framework从Required（添加framework默认为此）改为optional。


[iOS开发 .framework的Optional(弱引用)和Required(强引用)区别](http://www.cnblogs.com/wanyakun/p/3494323.html)




[Apple Watch三个月开发的一些收获总结](http://jerryliu.org/ios%20programming/Apple%20Watch-Development-summary/)

[watchOS 2](http://beyondvincent.com/2015/10/16/2015-10-16-watchkit-for-watchos-2/
)

http://bbs.feng.com/read-htm-tid-9101476.html

https://developer.apple.com/library/ios/samplecode/Lister/Introduction/Intro.html

[Apple Watch 编程指南（中文版）－极客学院](http://wiki.jikexueyuan.com/project/apple-watch-programming-guide/)

[Apple Watch开发专题](http://www.cocoachina.com/applewatch/)

[Apple Watch 指南-github](https://github.com/ipader/SwiftGuide/tree/master/Apple%20Watch)