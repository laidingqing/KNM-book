# 什么是微服务?

![微服务](/assets/images/microservice01.png)

作者未从软件架构层面讲述微服务，要了解架构方面内容，推荐[Enterprise Java Microservices](https://livebook.manning.com/book/enterprise-java-microservices/chapter-1/)

* 是一种小型的，松散耦合的分布式服务
* 作为解决可扩展性，独立性的解决方案
* SOA

## 解决的问题

* JVM没有内置资源管理
* 应用更新与修补对其它应用的影响
* 各应用版本控制独立性
* 单应用的稳定性决定了整体项目应用程序
* 失去了对特别基础设计优化的条件

## 不仅是拆分，还需遵循隔离原则

![微服务](/assets/images/microservices.png)

## 建议

* 因地制宜的使用微服务架构
* 小团队，小项目没有必要
* 微服务架构应结合完整的CI/DI流程，如Gitlab、Github、Jenkins等
* 生产资源在架构计时就应考虑