---
weight: 5
title: "链路追踪设计"
---
# 链路追踪设计


## Tracing
项目的链路追踪，项目内部内置了美团的cat作为项目的链路追踪服务，catMQ的客户端和服务端支持Cat自动打点，如果自己公司内部也使用了cat的话，只要在pom中引入cat-client即可自动开始打点。
如果不使用cat,也不用担心，只要不引入cat-client,catMQ是不会启动cat-client打点的
或者可以使用Skywalking(may force be with you),使用javaagent 的方式用来监控链路
其他的链路追踪软件出于时间资源的考虑，没有对应测试，欢迎大家提供其他的链路追踪方案

## Metrics
性能监控上，catMQ自动集成了Metrics，Metrics在项目中，主要用来监控消息的数量，若公司内部有搭建Promethues 的话，只要在pom 中引入micrometer-registry-Influx的依赖，将Metrics 的数据导入即可