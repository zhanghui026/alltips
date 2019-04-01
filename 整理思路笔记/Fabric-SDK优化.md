# Fabric JavaSdk优化

## 1.背景和目标

fabric-javasdk sdkIntegration目前作为hyperledger和应用层之间的桥梁，发现存在以下优化空间和优化方向。

目前

1) grpc 作为单连接，无连接池，无法保持长连接，在初次请求时会建立很长的连接时间。

2) 本机在访问除第一次上链后都是60ms左右，但是高并发后，会出现transactional等待问题，提升不了并发，解决此问题，可以使用多线程并发方式或者异步rxJava响应式编程方式，使用响应式编程的好处，





1）hfClient 连接池？

2）RxJava Or Coroutines(kotlin)

3） 背压策略选择提升吞吐问题。提供背压放弃方式、背压缓存内存方式进行背压方面的倍数

4） 高吞吐采用缓存方式 leveldb?

5） 配置和易用性

6） grpc优化

## 2. 解决方案

#### 2.1 hfClient连接池？

**结论：没必要使用连接池。**



hyper-ledger sdk使用的是gRPC，gRPC本身是个非常健壮，高并发的协议。

hfClient（hyperledger fabric client）grpc访问方式为NIO多路复用。多路复用NIO无需采用连接池，并且gRPC足够强壮使用http/2方式保持长连接以及高并发支持。（A Robust, High Performance Protocol）,并且有心跳和keep alive检测。

grpc 介绍 https://grpc.io/blog/grpc_on_http2



grpc 服务端-netty较大的吞吐



未来优化，多服务端（load balance）？，多客户端（sdk作为rest-server的方式）

#### 2.2 性能分析

#### 2.2.1 批量invoke操作sdk分析



##### channel init 操作

以下是单节点记录的耗时时间片

```create client:521
create channel client:79
create peer:13
create order:1
channel init:2191
```

比较耗时操作：channel init  >> create channel client

解决方式：channel 通过配置创建，为启动时唯一配置，当请求来临时，找到对应的channel进行操作。



##### send tx 操作

```toJson:17
createTrans:1
sendTxProposal:57
peerAdd:1
createTransOption1
sendTrans698
```

比较耗时操作：  sendTrans >> sendTxProposal

解决方式：sendTxProposal与sendTrans做并发，使用背压，通知send操作暂停



### 3.  batch save优化实施

batch save调用的sdk的invoke接口，主逻辑两个步骤（创建通道）channel init，（提交交易)send trans 

####  3.1 channel init 逻辑









