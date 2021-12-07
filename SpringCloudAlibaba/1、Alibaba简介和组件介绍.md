## 1、什么是SpringCloudAlibaba

阿里云为分布式应用开发提供了一站式解决方案，它包含了开发分布式应用所需的所有组件，使您可以轻松的使用springcloud开发应用程序。

有了阿里云，你只需要添加一些注解和少量的配置，就可以将Spring云应用连接到阿里的恩不是解决方案上，用阿里中间件搭建一个分布式应用系统。

## 2、提供的组件集

### 2.1 Flow control and service degradation

服务流量控制和服务降级（熔断）

Sentinel -> 替换springcloud原有的Hystrix组件

### 2.2 Service registration and discovery

服务注册与发现组件

Nacos -> 替换springcloud consul 和 eureka组件

### 2.3 Distributed Configuration

统一配置中心组件

Nacos -> 替换springcloud config组件 自动配置刷新

### 2.4 Event-driven

事件驱动 利用 MQ RocketMQ

事件驱动 -> 替换Bus组件实现消息总线

### 2.5 Message Bus

消息总线，异步处理

### 2.6 Distributed Transaction

分布式事务 Seata

### 2.7 Dubbo RPC

集成Dubbo实现服务间通信，实现RPC通信

## 3、微服务项目开发方案

目前微服务项目开发中的技术方案如下：

1、服务注册中心使用Nacos

2、服务间通信负载均衡使用HttpRest，a RestTeplate + Ribbon b OpenFeign

3、服务流控和服务降级 Sentinel

4、服务网关组件，Gateway

5、统一配置中心组件 Nacos

## 4、SpringCloudAlibaba 环境搭建

### 4.1 创建全局父项目

维护SpringCloud依赖，版本 Hoxton.SR6

维护alibaba依赖，版本2.2.1.RELEASE

集成springboot父项目，2.2.5.RELEASE

### 4.2 父项目依赖维护

```xml
<!--    继承springboot父项目-->
    <parent>
        <artifactId>spring-boot-starter-parent</artifactId>
        <groupId>org.springframework.boot</groupId>
        <version>2.2.5.RELEASE</version>
    </parent>

<!--    定义版本号-->
    <properties>
        <spring.cloud.version>Hoxton.SR6</spring.cloud.version>
        <spring.cloud.alibaba.version>2.2.1.RELEASE</spring.cloud.alibaba.version>
    </properties>

    <dependencyManagement>
        <dependencies>
<!--            维护springcloud-->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>${spring.cloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
<!--            维护springcloud alibaba-->
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${spring.cloud.alibaba.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
```

