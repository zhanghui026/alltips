# 区块链VolgaOpenApi 对接方式



## 0 对接准备

 对接准备，需要注册，并且选择对接方式，不同对接方式，联调成本不同。

注册应用服务：应用服务需提供唯一的服务名**sid**(区分其他openAPI提供的服务,此服务名为英文字母组成的服务名)，注册对接方式。

区块链VolgaOpenApi 可为应用服务提供多个独立空间（**独立账本**）。每个空间有唯一的访问标识**volgaKey**，应用服务提供独立的空间，若应用服务需要多个不同空间，需要多个volgaKey，volgaKey下数据为独立空间（**独立账本**）。

VolgaOpenApi提供俩种对接方式。

1.回调方式：VolgaOpenAPI需要**服务提供回调接口**验证volgaKey，VolgaOpenAPI在链请求时，会向服务方验证volgaKey。

2.用户注册：VolgaOpenApi提供api，注册用户和volgaKey（用户与volgaKey是多对多方式），VolgaOpenAPI返回volgaToken，请求时，需带上volgaKey和volgaToken。



##1.回调方式

应用方需管理volgaKey，提供回调接口验证volgaKey的有效性。

### 1.1  volgaKey验证

 应用服务与Header中请求参数应提供参数有volgaKey,sid。

* volgaKey: 应用服务的提供的数据隔离key串，不同的volgaKey有隔离的空间。（此key非上链数据的业务key）
* sid：服务方标识

### 1.2 调用步骤

 请求header带volgaKey进行访问区块链VolgaOpenAPI，区块链VolgaOpenAPI查询是否需要回调验证volgaKey，则调用应用服务的验证volgaKey接口，若验证成功，区块链API会将数据请求返回链请求结果。主要步骤为：

​    1.Header传volgaKey,sid进行接口调用

​    2.判断是否volgaKey需要回调.若需要回调应用服务，步骤3，否则步骤5

​    3.区块链VolgaOpenAPI访问服务的回调接口，验证volgaKey的有效性

​    4.返回验证成功

​    5.返回链请求结果

```sequence
应用服务->VolgaOpenAPI: 1.Header传volgaKey进行接口调用
Note right of VolgaOpenAPI: volgaKey下的数据为隔离的。
VolgaOpenAPI-->VolgaOpenAPI: 2.判断是否volgaKey需要回调.\n若需要回调，步骤3，否则步骤5
VolgaOpenAPI-->应用服务: 3.访问服务的回调接口，验证volgaKey的有效性
Note left of 应用服务: 验证volgaKey接口。
应用服务-->VolgaOpenAPI: 4.返回验证成功
VolgaOpenAPI->应用服务: 5.返回上链数据
```

### 1.3 总结

* 用户管理与volgaKey需要应用方设计。
* 对接回调方式，增加了对接成本。

## 2.  VolgaOpenApi管理用户注册

### 2.1 注册和管理Volga UAA

openAPI提供注册和管理api key的uaa，申请空间，volgaKey,将userId、sid注册到服务表中。

### 2.2 服务与OpenAPI调用

* 注册和申请volgaKey：VolgaOpenApi提供注册sid接口，返回一个新的volgaKey。（jwt授权权限调用Volga UAA）

- 注册用户到volgaKey：注册用户与volgaKey是多对多关系。返回volgaToken，可提供销毁之后支持。（jwt授权权限调用Volga UAA）
- 查询volgaToken：提供查询接口查询volgaToken。（jwt授权权限调用VolgaUAA）
- 请求链操作:header提供volgaToken，sid方式请求
- 链返回

```sequence
应用服务-->Volga UAA: 1.申请volgaKey：传sid
Volga UAA-->应用服务: 2.返回volgaKey
应用服务-->Volga UAA: 3.注册和查询：userId，volgaKey
Volga UAA-->应用服务: 4.应用服务: 返回volgaToken
应用服务->VolgaOpenAPI: 5.header传volgaToken，sid上传数据
VolgaOpenAPI->应用服务: 6.返回链请求
```

### 2.3 总结

* 应用方通过方式2，VolgaUAA 避免回调接口开发。减少网络麻烦。
* 应用方不必管理链UAA。









