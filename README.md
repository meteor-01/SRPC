# SRPC
## 使用Netty+Nacos+Protobuf制作RPC框架

### 这个RPC实现了一些基本的功能：

● 使用Netty来进行网络传输，效率比起传统的NIO要高很多。

● 使用单例模式，在Netty获取Channel的过程中，会有一个ChannelProvider去提供Channel单例。

● 使用Nacos作为服务的注册中心，用于管理注册的服务，当客户端请求发过来时，Nacos会寻找合适的服务返回给客户端消费。

● 实现了负载均衡的功能，，客户端对于Nacos返回的服务列表，会使用负载均衡算法，选择一个自己需要的服务加入，目前实现了轮询算法和随机选取算法。

● 加入了心跳检测机制，并不会发送完消息立即结束，而是保持的长连接，提高效率。

● 使用Potobuf作为对象的的序列化工具，实现Netty中的编/解码的功能，提高了效率。

● 实现了钩子函数，当服务端下线的时候会自动去Nacos注销服务。

● 使用CompletableFuture来接受客户端返回的结果。




### 测试

由于使用Nacos，调试比较简单：

下载好Nacos，无论是win版还是linux版，在官网都有，比较方便；

但是由于Nacos一般都要配置数据库，为了方便测试，可以使用命令先进行单机运行


startup.cmd -m standalone
