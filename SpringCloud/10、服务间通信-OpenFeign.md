## 1、概述

Feign是一个声明式的伪Http客户端，它似的写Http客户端变得更加简单，使用Feign，只需要创建一个接口并注解，它具有可插拔的注解特性（可以使用springmvc的注解），可使用Feign注解和JAX-RS注解，Feign支持可插拔的编码器和解码器。Feign默认集成了Ribbon，默认实现了负载均衡的效果并且springcloud为feign添加了springmvc注解的支持。

## 2、使用

### 2.1 创建两个独立的soringboot应用，并注册到服务注册中心 consul

引入依赖

```xml
<!--springboot-->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<!--健康轮训-->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-consul-discovery</artifactId>
</dependency>
```

修改配置

```yml
server:
  port: 8901

spring:
  cloud:
    consul:
      host: localhost
      port: 8500
      discovery:
        hostname: 127.0.0.1
  application:
    name: OPENFEIGN-PRODUCTCLIENT
```

入口类添加注解

```java
@SpringBootApplication
@EnableDiscoveryClient
public class OpenfeignProductApplication {

    public static void main(String[] args) {
        SpringApplication.run(OpenfeignProductApplication.class,args);
    }
}
```

### 2.2 使用OpenFeign

引入依赖

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-consul-discovery</artifactId>
</dependency>

<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>

<!--openfeign-->
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-openfeign</artifactId>
  <version>2.2.3.RELEASE</version>
</dependency>
```

添加注解

```java
@SpringBootApplication
@EnableDiscoveryClient //开启服务注册
@EnableFeignClients  //开启OpenFeign客户端调用
public class OpenFeignUserApplication {

    public static void main(String[] args) {
        SpringApplication.run(OpenFeignUserApplication.class,args);
    }
}
```

新建接口加注解

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
    @RequestMapping("/product/test1")
    String test1();

    @RequestMapping("/product/test2")
    String test2(@RequestParam("name") String name, @RequestParam("psw") String psw);

    @RequestMapping("/product/test3")
    String test3(@RequestBody Test test);

    @RequestMapping("/product/test4")
    Test test4();
}
```

## 3、OpenFeign参数传递

### 3.1 queryString 和 路径传参

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
  	//当你是一个参数的时候 可以不加@RequestParam("name") 但是不建议这么做 这个时候相当于默认添加了@RequestParam
    @RequestMapping("/product/test1")
    String test1(String name);
  	//如果是路径参数 那么使用@PathVariable
    @RequestMapping("/product/test1/{user_id}")
    String test1(@PathVariable("user_id") String user_id);
		//多参数的时候 一定要加注解 否则运行报错
    @RequestMapping("/product/test2")
    String test2(@RequestParam("name") String name, @RequestParam("psw") String psw);
		//无参形式
    @RequestMapping("/product/test4")
    String test4();
  	//如果你明确知道请求方式 也可使用对应的GetMapping或者PostMapping或者其他
    @GetMapping("/product/test5")
    String test5();
    @PostMapping("/product/test6")
    String test6();
}
```

### 3.2 传递对象参数

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
		//传递对象的时候 如果需要使用传递json格式 一定要添加@RequestBody
    @RequestMapping("/product/test3")
    String test3(@RequestBody Test test);
}
```

### 3.3 数组和集合

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
  	//传递数组 在url中传递的方式应该是 ?ids=1&ids=2&ids=3 必须添加@RequestParam
		@PostMapping("/product/test7")
    String test7(@RequestParam("ids") String[] ids);
  	//传递集合 springmvc不能直接接受 如果想要接手 必须要将集合放在对象中再接收
}
```

## 4、服务间通信的响应处理

### 4.1 返回对象

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
    //返回对象
  	@RequestMapping("/product/test9")
    Test test9();
    //返回集合
  	@RequestMapping("/product/test10")
    List<Test> test10();
} 
```

### 4.2 返回字符串

```java
@FeignClient(value = "OPENFEIGN-PRODUCTCLIENT") //value注明调用的服务id
public interface ProductClient {
    //返回对象
  	@RequestMapping("/product/test9")
    String test9();
} 
```

## 5、OpenFeign超时处理

### 5.1 默认超时处理

使用OpenFeign组件在进行服务间通信时要求被调用服务必须在1s内基于响应，一旦服务执行业务逻辑时间超过1s，OpenFeign组件将直接报错Read Timeout

### 5.2 修改OpenFeign超时时间

#### 5.2.1 指定服务修改某一个服务的调用超时时间

```properties
feign.client.config.PRODUCTS.connectTimeout=5000 #配置指定服务连接超时时间 其中PRODUCTS是服务id
feign.client.config.PRODUCTS.readTimeout=5000 #配置指定服务等待超时时间 其中PRODUCTS是服务id
```

#### 5.2.2 修改openfeign默认调用所有服务超时时间

```properties
feign.client.config.default.connectTimeout=5000 #配置所有服务连接超时时间
feign.client.config.default.readTimeout=5000 #配置所有服务等待超时时间
```

## 6、OpenFeign日志展示

OpenFeign 是一个伪HttpClient客户端对象，用来帮助我们完成服务间通信，底层用http协议，完成服务间调用。

日志：OpenFeign为了更好方便在开发过程中调试OpenFeign数据传输，和响应处理，添加了日志功能。 OpenFeign对日志的处理非常灵活可以为每个OpenFeign客户端指定日志记录策略，每个客户端都会创建一个logger，默认情况下logger的名称是OpenFeign的全限定名，需要注意的是，OpenFeign的日志打印只会对DEBUG级别做出响应。

我们可以为OpenFeign客户端配置各自的logger.level对象，告诉OpenFeign记录哪些日志，logger.level有以下的几种值。

```apl
NONE 不记录任何日志
BASIC 仅仅会记录请求方法，url，响应状态和执行时间
HEADERS 记录Basic级别的基础上，记录请求和响应的header
FULL 记录请求和响应的header,body和元元素
```

###  6.1 配置展示日志

```properties
# 对客户端进行debug日志响应
logging.level.com.cretin.feignclient=debug
# 对指定服务id进行日志监控
feign.client.config.PRODUCTS.loggerLevel=FULL 
# 对所有的服务进行日志监控
feign.client.config.default.loggerLever=FULL
```



