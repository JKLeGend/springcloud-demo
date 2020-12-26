# This is a SpringCloud demo with SkyWalking and Prometheus;

## 简介

demo基于Spring Cloud Greenwich, 集成了springcloud大部分核心组件, 包括Spring Cloud Eureka, Gateway, Ribbon, Hystrix, Config; 项目采用上述基础组件搭建, 并未使用Zuul, OpenFeign等集成组件, 也未使用Bus做配置自动刷新等其他特性, 未探讨Nacos, Consul等其他组件方案, 仅用以演示微服务基础架构;

## 项目结构

![系统架构图](micro_service_arch.jpg)

## 项目结构

``` lua
springcloud-demo
├── client-service -- 核心业务服务
├── common -- 公共模块
├── eureka -- 注册中心,服务注册与发现
├── config -- 配置中心服务
├── gateway -- 网关服务
├── ribbon -- 负载均衡服务
└── hystrix -- 服务降级与熔断服务
```

### 搭建步骤
> Docker环境部署
- prometheus: [http://localhost:9090/classic/targets](http://localhost:9090/classic/targets)
```
docker pull prom/prometheus
docker run -d \
    -p 9090:9090 \
    --name prometheus \
    -v "/$(pwd)/resources/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml" \
    prom/prometheus
```
- grafana: [http://localhost:9090](http://localhost:9090) 用户名密码-admin/admin
```
docker pull grafana/grafana
docker run -d \
  -p 9099:3000 \
  --name grafana \
  -v "/$(pwd)/resources/grafana/grafana-storage:/var/lib/grafana" \
  grafana/grafana
```
- skywalking: [http://localhost:13800](http://localhost:13800)
```
docker pull apache/skywalking-oap-server
docker run \
  -p 11800:11800 \
  -p 12800:12800 \
  --name skywalking-oap-server \
  --restart always \
  apache/skywalking-oap-server

docker pull apache/skywalking-ui
docker run \
  -p 13800:8080 \
  --name skywalking-ui \
  --restart always \
  --link skywalking-oap-server \
  -e SW_OAP_ADDRESS=skywalking-oap-server:12800 \
  apache/skywalking-ui
```