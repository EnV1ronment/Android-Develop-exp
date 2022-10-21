# Android-Develop-exp
在Gradle 7+版本中，不安全HTTP连接，需要我们指定布尔allowInsecureProtocol。
maven {
    allowInsecureProtocol = true
    ...      
}

超出容器外部的点击事件不会响应

# RN-Develop-exp
RN前端与原生模块之间通信方式
（1）使用回调函数Callback，它提供了一个函数来把返回值传回给JavaScript。
（2）使用Promise来实现。
（3）原生模块向JavaScript发送事件
Callback

问题
1.callback并非在对应的原生函数返回后立即被执行
2.因为跨语言通讯是异步的，这个执行过程会通过消息循环来进行。 
3.当我们在前端调用原生函数后，原生函数的返回值可能还没有得出，然而已经在执行Callback了
4.所以我们并不能得到准确的返回值。因为回调函数Callback 对原生模块 来说是被动的，由前端来主动调用回调函数，然后得到返回值，实现原生模块和前端的数据交互。

Promise

优点
语法简单，易于使用
缺点
1.反复回调
   在某些情况下会存在需要嵌套的情况，此时使用promise会导致回调金字塔现象，对分析和程序跳转掌控减弱，且promise的catch对反复回调加深理解难度。
2.重复调用
   在某些情况下，需要对某功能进行多次使用，除了反复编写外，使用for等循环语句时代码出错或逻辑混乱
   
Event

实现方式：
1.原生模块向JavaScript发送事件则是一种主动机制。
2.当原生函数执行到任何一步时都可以主动向前端发送事件。
3.前端需要监视该事件，当前端收到某确定事件时，则可根据收到事件类型进行对应操作
优点

1.逻辑清晰
2.主动反馈，不会出现返回值不准确现象
3.事件位置可用于代码任意位置，易于扩展

缺点

1.需要前端设置监听器
2.主动反馈不可过度且频繁，从使用上来看，过度频繁后会导致设备出现宕机状态，具体原因待分析
3.不建议设置过多事件监听器


使用navigator.geolocation.getCurrentPosition 获取android定位时 不采用高精度定位 enableHighAccuracy: false 容易超时影响用户体验
# IOS-Develop-exp

Could not launch app
failed to get the task for process
证书出了问题 使用自动配置证书可临时解决问题
