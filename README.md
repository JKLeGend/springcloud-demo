# Welcome!
## This is a SpringCloud demo with SkyWalking and Prometheus;

## 简介

demo基于Spring Cloud Greenwich, 集成了springcloud大部分核心组件, 包括Spring Cloud Eureka, Gateway, Ribbon, Hystrix, Config; 项目采用上述基础组件搭建, 并未使用Zuul, OpenFeign等集成组件, 也未使用Bus做配置自动刷新等其他特性, 未探讨Nacos, Consul等其他组件方案, 仅用以演示微服务基础架构;

## 项目结构

![系统架构图](SOA-MS-SPRINGCLOUD.png)

## 项目结构

``` lua
springcloud-demo
├── client-service -- 核心业务服务
├── common -- 公共模块
├── eureka -- 注册中心,服务注册与发现
├── config -- 配置中心服务
├── gateway -- 网关服务
├── ribbon -- 负载均衡服务
├── hystrix -- 服务降级与熔断服务
└── resources -- 第三方服务配置及中间文件
```
### 编译
```
mvn clean install -DskipTests
```
### 运行
> 请确保本机端口8000,8001,8002,8003,8004,9001未被占用;
```
COMPOSE_HTTP_TIMEOUT=500 docker-compose up
COMPOSE_HTTP_TIMEOUT=500 docker-compose -f docker-compose-monitor.yml up
```
### 测试
- eureka服务器地址: [http://localhost:8001](http://localhost:8001)
- client-service客户端服务api文档地址: [http://localhost:8000/swagger-ui.html#/](http://localhost:8000/swagger-ui.html#/)
- 测试api全链路请求地址: [http://localhost:9001/user/1](http://localhost:9001/user/1)
- gateway服务器地址: [http://localhost:9001](http://localhost:9001)
- ribbon服务器地址: [http://localhost:8002](http://localhost:8002)
- hystrix服务器地址: [http://localhost:8003](http://localhost:8003)
- prometheus服务地址: [http://localhost:9090/classic/targets](http://localhost:9090/classic/targets)
- grafana服务地址: [http://localhost:9099/](http://localhost:9099/) 用户名密码-admin/admin
- skywalking服务地址: [http://localhost:13800/](http://localhost:13800/)
