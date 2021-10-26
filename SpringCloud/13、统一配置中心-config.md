## 1、概述

config又称为统一配置中心，就是将配置统一管理，配置统一管理的好处是在日后大规模集群部署服务应用时相同的服务配置一致，后面再需要修改的时候统一修改全部配置，不需要一个一个服务手动维护。

![image-20211025091958343](./images/image-20211025091958343.png)

## 2、使用

### 2.1 server 配置

#### 2.1.1 引入依赖

```xml
<!--        springboot应用-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

<!--        管理中心-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-consul-discovery</artifactId>
        </dependency>

<!--        健康管理-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

<!--        config配置中心-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-config-server</artifactId>
        </dependency>
```

#### 2.1.2 配置配置文件

```yml
server:
  port: 8848

spring:
  cloud:
    consul:
      host: localhost
      port: 8500
      discovery:
        hostname: 127.0.0.1
    # 配置统一配置中心
    config:
      server:
        git:
          uri: https://gitee.com/mxnzp/springcloud-config.git # 仓库地址
          default-label: master # 默认分支
          username: xxxx # git仓库的账户
          password: xxxx # git仓库的密码

  application:
    name: CONFIGSERVER

```

#### 2.1.3 开启统一配置中心

```java
@SpringBootApplication
@EnableDiscoveryClient
@EnableConfigServer //我是一个统一配置中心
public class ConfigServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(ConfigServerApplication.class,args);
    }
}
```

### 2.2 client 配置

![image-20211025094206943](/images/image-20211025094206943.png)