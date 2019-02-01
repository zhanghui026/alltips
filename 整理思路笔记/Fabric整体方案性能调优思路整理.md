<head> 
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/all.js"></script> 
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/v4-shims.js"></script> 
</head> 
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.0.13/css/all.css">

## Fabric 性能调优方案整理


### 性能调优三个入手方面

* fabric 底层优化： <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
* fabric SDK层和rest层：<i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
* 应用层： <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>


###  fabric底层优化计划

 2月至4月完成

* 优化点
  * 底层上链
  * 读取优化
  * 调优参数优化设置
  * 底层原理优化

<p />


* 使用工具
  * fabric
  * kafka
  * leveldb
  * couchdb
  * redis
  * jmeter
  * rabbitmq


### SDK层和rest层

2月至3月完成

#### SDK 优化方式
* JAVA SDK源码层和SDK源码封装层调研
* Netty引入

### rest层

* rest，go实现或者netty nio模型实现对比

### 使用工具

* gatling-chart
* jmeter
* netty-nio
* java-sdk 源码
* rest ，spring-flux
* go， go-restful

### 应用层

使用非阻塞模型 （2月完成）
* spring层使用方式推荐webFlux 
* webClient替换restTemplate







