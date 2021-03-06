### dubbo通信过程
关注几个问题点：

1. 基于什么协议实现的？
2. 客户端怎么发起请求？
3. 怎么讲请求转化成符合协议的格式的？
4. 传输协议是什么样的？
5. 服务端端怎么接收请求？
6. 服务端到数据了怎么将流转化为原来的格式？
7. 处理完成后怎么回应给客户端？

>
- 默认采用netty协议
- 将请求封装到RpcInvocation对象中，通过netty进行传送
- 对象序列化
- netty本身的nio及socket
- netty的响应机制
- 反序列化
- 回应内容封装成RpcResult对象，序列化后通过netty传输给客户端。


### 优先级
1. 方法级别优先-》接口-》全局配置。
2. 如果级别一样，客户端优先。

### 什么是SPI
1. META-INF/services/接口全路径文件
![](https://i.imgur.com/U6MuKp5.png)


@Adaptive

- 在类上，直接加载当前的适配器
- 在方法上，动态创建一个自适应的适配器




### 利用Hold对象
>学会使用Hold类似的模式写代码。。。

### 适配器模式
>Protocol$Adaptive等等，可以动态创建自适应适配器，通过URL的参数判断适配器的类型。

### 注册provider服务

jvm内部调用

>1. 暴露一个接口给jvm内部调用

暴露服务给外部调用

>1. 本地端口监听
2. 注册到zookeeper
3. 订阅服务的改变事件

### 调用服务时
1. urls.size() == 1??????
2. invoker === MockClusterInvoker
3. 通过invoker创建代理服务进行调用。
4. proxy0.sayHello() ===>handler.invoke()

### 监控中心的使用流程？
1. 源码分析
2. 日志 权限（过滤器？）