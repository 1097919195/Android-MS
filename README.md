

# Android 高级面试

### ![面试](img/面试.png)写给Android的一封信

最近半年，常常有人问我 “Android就业市场究竟怎么样，我还能不能坚持下去 ?”

现在想想，移动互联网的发展不知不觉已经十多年了，Mobile First 也已经变成了 AI First。换句话说，我们已经不再是“风口上的猪”。移动开发的光环和溢价开始慢慢消失，并且正在向 AI、区块链等新的领域转移。移动开发的新鲜血液也已经变少，最明显的是国内应届生都纷纷涌向了 AI 方向。

​       可以说，国内移动互联网的红利期已经过去了，现在是增量下降、存量厮杀，从争夺用户到争夺时长。比较明显的是手机厂商纷纷互联网化，与传统互联网企业直接竞争。另外一方面，过去渠道的打法失灵，小程序、快应用等新兴渠道崛起，无论是手机厂商，还是各大 App 都把出海摆到了战略的位置。



**各大培训市场也不再培训Android，作为开发Android的我们该何去何从？**



​        其实如果你技术深度足够，大必不用为就业而忧愁。每个行业何尝不是这样，最开始的风口，到慢慢的成熟。Android初级在2019年的日子里风光不再， 靠会四大组件就能够获取到满意薪资的时代一去不复返。**经过一波一波的淘汰与洗牌，剩下的都是技术的金子。就像大浪褪去，裸泳的会慢慢上岸。**而真正坚持下来的一定会取得不错成绩。毕竟Android市场是如此之大。从Android高级的蓬勃的就业岗位需求来看，能坚信我们每一位Android开发者的梦想 。

 接下来我们针对Android高级展开的完整面试题 



## ---------------------预习专区-----------------------

- [Android预习专题](./android/README.md)
  - [手把手带你深入分析 Handler](study/framework/Android消息机制.md)
  - [Android 消息机制——你真的了解Handler？](./study/framework/Handler机制源码.md)



## ---------------------2019Android年高级面试---------------------- 

 * [2019年Bat面试集合](#2019年Bat面试集合)
 * [Java 核心](#java-核心)
 * [Android 核心](#android-核心)
 * [架构](#架构)
 * [设计问题](#设计问题)
 * [工具和技能](#工具和技能)
 * [Android 测试驱动开发](#android-测试驱动开发)
 * [其他](#其他)


### 2019年Bat面试集合

> 数据结构与算法问题的难度完全取决于你所申请的公司

* [谈谈线程池原理](android/thread.md)




### Java 核心



  ```

- 枚举和迭代器有什么区别？



  1. 函数接口不同：
Enumeration只有2个函数接口。通过Enumeration，我们只能读取集合的数据，而不能对数据进行修改。
Iterator只有3个函数接口。Iterator除了能读取集合的数据之外，也能数据进行删除操作。
  2. Iterator支持fail-fast机制，而Enumeration不支持。
Enumeration 是JDK 1.0添加的接口。使用到它的函数包括Vector、Hashtable等类，这些类都是JDK 1.0中加入的，Enumeration存在的目的就是为它们提供遍历接口。Enumeration本身并没有支持同步，而在Vector、Hashtable实现Enumeration时，添加了同步。
而Iterator 是JDK 1.2才添加的接口，它也是为了HashMap、ArrayList等集合提供遍历接口。Iterator是支持fail-fast机制的：当多个线程对同一个集合的内容进行操作时，就可能会产生fail-fast事件。
  


- Java 中 *fail-fast* 和 *fail-safe* 的区别？

- 什么是 Java 优先级队列？

- 什么是设计模式 [Link](https://github.com/iluwatar/java-design-patterns)


### Android 核心

* 阐述一下 Activity 的生命周期。

创建 onCreate -  启动onStart – 开始 onResume – 暂停 onPause – 结束 onStop – 销毁onDestroy

每一个活动（ Activity ）都处于某一个状态，对于开发者来说，是无法控制其应用程序处于某一个状态的，这些均由系统来完成。 
但是当一个活动的状态发生改变的时候，开发者可以通过调用 onXX() 的方法获取到相关的通知信息。 

在实现 Activity 类的时候，通过覆盖（ override ）这些方法即可在你需要处理的时候来调用。 

•onCreate ：当活动第一次启动的时候，触发该方法，可以在此时完成活动的初始化工作。 
onCreate 方法有一个参数，该参数可以为空（ null ），也可以是之前调用 onSaveInstanceState（）方法保存的状态信息。

•onStart ：该方法的触发表示所属活动将被展现给用户。 

•onResume ：当一个活动和用户发生交互的时候，触发该方法。 

•onPause ：当一个正在前台运行的活动因为其他的活动需要前台运行而转入后台运行的时候，触发该方法。这时候需要将活动的状态持久化，比如正在编辑的数据库记录等。 

•onStop ：当一个活动不再需要展示给用户的时候，触发该方法。如果内存紧张，系统会直接结束这个活动，而不会触发 onStop 方法。 所以保存状态信息是应该在onPause时做，而不是onStop时做。活动如果没有在前台运行，都将被停止或者Linux管理进程为了给新的活动预留足够的存储空间而随时结束这些活动。因此对于开发者来说，在设计应用程序的时候，必须时刻牢记这一原则。在一些情况下，onPause方法或许是活动触发的最后的方法，因此开发者需要在这个时候保存需要保存的信息。 

•onRestart ：当处于停止状态的活动需要再次展现给用户的时候，触发该方法。 

•onDestroy ：当活动销毁的时候，触发该方法。和 onStop 方法一样，如果内存紧张，系统会直接结束这个活动而不会触发该方法。 

•onSaveInstanceState ：系统调用该方法，允许活动保存之前的状态，比如说在一串字符串中的光标所处的位置等。 
通常情况下，开发者不需要重写覆盖该方法，在默认的实现中，已经提供了自动保存活动所涉及到的用户界面组件的所有状态信息。
  

* 谈谈 Android 的四大组件。

1. 活动：

Android 中，Activity是所有程序的根本，所有程序的流程都运行在Activity 之中，Activity可以算是开发者遇到的最频繁，也是Android 当中最基本的模块之一。在Android的程序当中，Activity 一般代表手机屏幕的一屏。如果把手机比作一个浏览器，那么Activity就相当于一个网页。在Activity 当中可以添加一些Button、Check box 等控件。可以看到Activity 概念和网页的概念相当类似。一般一个Android 应用是由多个Activity 组成的。这多个Activity 之间可以进行相互跳转，例如，按下一个Button按钮后，可能会跳转到其他的Activity。和网页跳转稍微有些不一样的是，Activity 之间的跳转有可能返回值，例如，从Activity A 跳转到Activity B，那么当Activity B 运行结束的时候，有可能会给Activity A 一个返回值。这样做在很多时候是相当方便的。
　　当打开一个新的屏幕时，之前一个屏幕会被置为暂停状态，并且压入历史堆栈中。用户可以通过回退操作返回到以前打开过的屏幕。可以选择性的移除一些没有必要保留的屏幕，因为Android会把每个应用的开始到当前的每个屏幕保存在堆栈中。 

2. 服务

Service 是android 系统中的一种组件，它跟Activity 的级别差不多，但是他不能自己运行，只能后台运行，并且可以和其他组件进行交互。Service 是没有界面的长生命周期的代码。Service是一种程序，它可以运行很长时间，但是它却没有用户界面。这么说有点枯燥，来看个例子。打开一个音乐播放器的程序，这个时候若想上网了，那么，打开Android浏览器，这个时候虽然已经进入了浏览器这个程序，但是，歌曲播放并没有停止，而是在后台继续一首接着一首的播放。其实这个播放就是由播放音乐的Service进行控制。当然这个播放音乐的Service也可以停止，例如，当播放列表里边的歌曲都结束，或者用户按下了停止音乐播放的快捷键等。Service 可以在和多场合的应用中使用，比如播放多媒体的时候用户启动了其他Activity这个时候程序要在后台继续播放，比如检测SD 卡上文件的变化，再或者在后台记录地理信息位置的改变等等，总之服务嘛，总是藏在后头的。

开启Service有两种方式:
（1） Context.startService（）：Service会经历onCreate -> onStart（如果Service还没有运行，则android先调用onCreate（）然后调用onStart（）；
　　　　如果Service已经运行，则只调用onStart（），所以一个Service的onStart方法可能会重复调用多次 ）；
　　　　StopService的时候直接onDestroy，如果是调用者自己直接退出而没有调用StopService的话，Service会一直在后台运行。该Service的调用者再启动起来后可以通过stopService关闭Service。
　　*注意:多次调用Context.startservice（）不会嵌套（即使会有相应的onStart（）方法被调用），所以无论同一个服务被启动了多少次，一旦调用Context.stopService（）或者StopSelf（），他都会被停止。
　　补充说明：传递给StartService（0的Intent对象会传递给onStart（）方法。调用顺序为：onCreate --> onStart（可多次调用) --> onDestroy。
（2） Context.bindService（）：Service会经历onCreate（） -->onBind（），onBind将返回给客户端一个IBind接口实例，IBind允许客户端回调服务的方法，比如得到Service运行的状态或其他操作。这个时候把调用者（Context，例如Activity）会和Service绑定在一起，Context退出了，Srevice就会调用onUnbind --> onDestroyed相应退出，所谓绑定在一起就共存亡了。

3. 广播接收器

在Android 中，Broadcast是一种广泛运用的在应用程序之间传输信息的机制。而BroadcastReceiver 是对发送出来的Broadcast进行过滤接受并响应的一类组件。可以使用BroadcastReceiver 来让应用对一个外部的事件做出响应。这是非常有意思的，例如，当电话呼入这个外部事件到来的时候，可以利用BroadcastReceiver 进行处理。例如，当下载一个程序成功完成的时候，仍然可以利用BroadcastReceiver 进行处理。BroadcastReceiver不能生成UI，也就是说对于用户来说不是透明的，用户是看不到的。BroadcastReceiver通过NotificationManager 来通知用户这些事情发生了。BroadcastReceiver 既可以在AndroidManifest.xml 中注册，也可以在运行时的代码中使用Context.registerReceiver（)进行注册。只要是注册了，当事件来临的时候，即使程序没有启动，系统也在需要的时候启动程序。各种应用还可以通过使用Context.sendBroadcast （） 将它们自己的Intent Broadcasts广播给其他应用程序。

4. 内容提供者

Content Provider 是Android提供的第三方应用数据的访问方案。
　　在Android中，对数据的保护是很严密的，除了放在SD卡中的数据，一个应用所持有的数据库、文件等内容，都是不允许其他直接访问的。Andorid当然不会真的把每个应用都做成一座孤岛，它为所有应用都准备了一扇窗，这就是Content Provider。应用想对外提供的数据，可以通过派生Content Provider类， 封装成一枚Content Provider，每个Content Provider都用一个uri作为独立的标识，形如：content://com.xxxxx。所有东西看着像REST的样子，但实际上，它比REST 更为灵活。和REST类似，uri也可以有两种类型，一种是带id的，另一种是列表的，但实现者不需要按照这个模式来做，给id的uri也可以返回列表类型的数据，只要调用者明白，就无妨，不用苛求所谓的REST。

* Service 与 IntentService 的区别。[Link](https://stackoverflow.com/a/15772151/5153275)

* Android 应用的结构是什么？

* Android 应用中如何保存数据。

* 如何在 Android 应用中执行耗时操作。

* 两个 Fragment 之间如何通信。

* 阐述一下 Android 的通知系统。

* 两个不同的 app 之间如何交互。

* 什么是 Fragment？

* 为什么建议只使用默认的构造方法来创建 Fragment？[Link](https://stackoverflow.com/a/16042750/2809326)

* 为什么 Bundle 被用来传递数据，为什么不能使用简单的 Map 数据结构？

* 阐述一下 Fragment 的生命周期。[Link](https://www.techsfo.com/blog/wp-content/uploads/2014/08/complete_android_fragment_lifecycle.png)

* 如何理解 Android 的 Dialog ？

* 解释下 Android 的 View 。

* 你能创建自定义 View 吗？具体是如何创建的？

* 什么是 ViewGroup ，它与 View 的区别在哪里？

* Fragment 和 Activity 有什么区别？它们之间又有什么关系？

* 谈谈 Serializable 接口和 Parcelable 接口的区别。在 Android 中最好使用哪种接口？

* Activity 的启动模式有哪些？[Link](https://blog.mindorks.com/android-activity-launchmode-explained-cbc6cf996802)

* 解释一下 Android 中的 Intent 。[Link](https://stackoverflow.com/questions/6578051/what-is-an-intent-in-android)

* 什么是隐式 Intent ？

* 什么是显式 Intent ？

* 解释一下 AsyncTask 。

* 如何理解 Android 中的广播。[Link](https://stackoverflow.com/questions/5296987/what-is-broadcastreceiver-and-when-we-use-it)

* 如何理解 Android 的 LocalBroadcastManager 。[Link](https://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)

* 什么是 JobScheduler ？[Link](http://www.vogella.com/tutorials/AndroidTaskScheduling/article.html)

* 什么是 DDMS ？你可以用它来做什么？

* 解释一下什么是 support libary ，以及为什么要引入 support library ？[Link](http://martiancraft.com/blog/2015/06/android-support-library/)

* 如何理解 Android 中的 ContentProvider 。它通常用来干什么？

* 什么是 Data Binding ？[Link](https://developer.android.com/topic/libraries/data-binding/index.html)

* Android 的核心组件具体都有什么？[Link](https://developer.android.com/topic/libraries/architecture/index.html)

* 什么是 ADB ？

* 什么是 ANR ？如何避免发生 ANR ？

* AndroidManifest.xml 是什么？

* 解释一下 broadcast 和 intent 在 app 内传递消息的工作流程。

* 当 Bitmap 占用较多内存时，你是怎么处理的？

* Android 应用有哪些不同的存储数据的方式？

* 什么是 Dalvik 虚拟机？

* AsyncTask 的生命周期和(它所属的) Activity 的生命周期有什么关系？这种关系可能会导致什么样的问题？ 如何避免这些问题发生？


* Intent filter 是用来做什么的？

* 什么是 Sticky Intent？[Link](http://www.androidinterview.com/what-is-a-sticky-intent/)

* 什么是 AIDL ？列举一下通过 AIDL 创建被绑定的服务（bounded service）的步骤。

* Android 的权限有多少个不同的保护等级？

* 在转屏时你如何保存 Activity 的状态？[Link](https://stackoverflow.com/questions/3915952/how-to-save-state-during-orientation-change-in-android-if-the-state-is-made-of-m)

* 相对布局和线性布局的区别。

* 如何实现 XML 命名空间？

* View.GONE 和 View.INVISIBLE 之间的区别。

* Bitmap 和 .9（nine-patch）图片之间有什么区别？

* 谈谈位图池。[Link](https://blog.mindorks.com/how-to-use-bitmap-pool-in-android-56c71a55533c)

* 在 Android 中如何避免内存泄漏？

* Android 桌面的小部件是什么？

* 什么是 AAPT ？

* 你是如何在 Android 应用程序中发现内存泄漏的？

* 你如何排查应用崩溃的原因？

* 为什么你应该避免在主线程上运行非用户界面相关的代码？

* 你是如何适配不同分辨率的手机的？

* 如何理解 Doze 模式。如何理解应用程序待机模式（App Standby）。

* 在 Android 中，你可以使用什么来进行后台操作?

* 什么是 ORM ？它是如何工作的？

* 什么是 Loader ？

* 什么是 NDK ，为什么它是有用的？

* 如何理解严格模式（StrictMode）。 [Link](https://blog.mindorks.com/use-strictmode-to-find-things-you-did-by-accident-in-android-development-4cf0e7c8d997)

* 什么是 Lint ？它的用途是什么？

* 什么是 SurfaceView ？

* ListView 和 RecyclerView 有什么区别？

* 什么是 ViewHolder 模式？为什么我们应该使用它？

* 什么是 PendingIntent ？

* 你能手动调用垃圾回收吗？

* 周期地更新页面的最好方式是什么？

* 有哪些类型的广播？

* 你开发过组件吗？请描述一下。[Link](https://blog.mindorks.com/android-widgets-ad3d166458d3)

* 如何理解上下文（Context）。怎么使用它？[Link](https://medium.com/p/understanding-context-in-android-application-330913e32514)

* 你知道什么是视图树(View Tree)吗？怎样优化它的深度？

* onTrimMemory() 方法是什么？

* Android 应用可以使用多进程吗？怎样使用？

* 内存溢出（OutOfMemory）是怎么发生的？

* 文本样式接口（Spannable）是什么？

* 什么是过度绘制（overdraw）？

* 什么是渲染脚本（renderscript）？[Link](https://blog.mindorks.com/comparing-android-ndk-and-renderscript-1a718c01f6fe)

* Dalvik 虚拟机模式和 ART（Android Runtime）虚拟机模式的区别。

* FlatBuffers 和 JSON 的区别。[Link](https://blog.mindorks.com/why-consider-flatbuffer-over-json-2e4aa8d4ed07)

* 谈谈 Android 的注解。[Link1](https://blog.mindorks.com/creating-custom-annotations-in-android-a855c5b43ed9), [Link2](https://blog.mindorks.com/improve-your-android-coding-through-annotations-26b3273c137a)

* 描述一下约束布局（Constraint Layout）。[Link](https://blog.mindorks.com/using-constraint-layout-in-android-531e68019cd)

* 阐述一下 Android 中的 HashMap , ArrayMap 和 SparseArray 。[Link](https://blog.mindorks.com/android-app-optimization-using-arraymap-and-sparsearray-f2b4e2e3dc47)

* 阐述一下 Looper, Handler 和 HandlerThread 。[Link](https://blog.mindorks.com/android-core-looper-handler-and-handlerthread-bd54d69fe91a)

* 如何降低 Android 应用的耗电量？[Link](https://blog.mindorks.com/battery-optimization-for-android-apps-f4ef6170ff70)

* SnapHelper 是什么？[Link](https://blog.mindorks.com/using-snaphelper-in-recyclerview-fc616b6833e8)

* 在 Android 中怎么处理多点触控？[link](https://arjun-sna.github.io/android/2016/07/20/multi-touch-android/)


### 架构

* 请介绍一下你做的上一个 App 的架构。

* 请介绍一下 MVP。 [Link](https://blog.mindorks.com/essential-guide-for-designing-your-android-app-architecture-mvp-part-1-74efaf1cda40)

* Presenter 是什么？

* 什么是模型？

* 请介绍一下 MVC。

* Controller 是什么？

* 请介绍一下 MVVM。 [Link](https://github.com/MindorksOpenSource/android-mvvm-architecture)

* 谈谈你对代码整洁之道（clean code）的理解。[Link](https://blog.mindorks.com/every-programmer-should-read-this-book-6755dedec78d)


### 设计问题

* 请设计 Uber App。

* 请设计 Facebook App。

* 请设计 Facebook Near-By Friends App。

* 请设计 WhatsApp。

* 请设计 SnapChat。

* 基于地理位置 App 的设计问题。


### 工具和技能

* Git. [Link](https://github.com/git-tips/tips)

* RxJava. [Link](https://blog.mindorks.com/a-complete-guide-to-learn-rxjava-b55c0cea3631)

* Dagger 2. [Link](https://medium.com/p/a-complete-guide-to-learn-dagger-2-b4c7a570d99c)

* Android 开发实用工具。 [Link](https://blog.mindorks.com/android-development-useful-tools-fd73283e82e3)

* Firebase. [Link](https://firebase.google.com/)


### Android 测试驱动开发

* Espresso 是什么？ [Link](https://developer.android.com/training/testing/ui-testing/espresso-testing.html)

* Robolectric 是什么？ [Link](http://robolectric.org/)

* UI-Automator 是什么？ [Link](https://developer.android.com/training/testing/ui-testing/uiautomator-testing.html)

* 请解释一下单元测试。

* 请解释一下设备化测试。

* 你是否做过单元测试或者自动测试？

* 为什么要使用 Mockito？ [Link](http://site.mockito.org/)

* 请描述一下 JUnit 测试。


### 其他

* 描述一下 REST APIs 如何工作 ？

* 描述一下 SQLite 。

* 描述一下 数据库 。

* 项目管理工具 - trello ，basecamp ，kanban ，jira ，asana 。

* 关于构建系统 - gradle , ant , buck 。

* APK 逆向工程 。

* 混淆器用于什么 ？

* 什么是混淆？ 用于什么？ 如何压缩 ？

* 如何构建你的发布版本的 APP ？

* 如何面向特定用户群体更新应用程序版本 ？

* 可以识别卸载我们的应用程序的用户吗 ？

* 缩小 APK 的体积 。[Link](https://blog.mindorks.com/how-to-reduce-apk-size-in-android-2f3713d2d662)

* Android 开发最佳实践 。[Link](https://blog.mindorks.com/android-development-best-practices-83c94b027fd3)

* Android 代码风格和指南 。[Link](https://blog.mindorks.com/android-code-style-and-guidelines-d5f80453d5c7)

* 你尝试使用过 Kotlin 吗 ？[Link](https://blog.mindorks.com/why-you-must-try-kotlin-for-android-development-e14d00c8084b)

* 开发 Android 应用程序时应该连续测量哪些指标 ？[Link](https://blog.mindorks.com/android-app-performance-metrics-a1176334186e)


### 贡献者
 

  ```
​    
