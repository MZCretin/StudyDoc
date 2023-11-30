## 1、简介

### 1.1 服务雪崩

在微服务之间进行服务调用时由于某一个服务故障，导致级联服务故障的现象，成为雪崩效应。雪崩效应藐视的数提供方不可用，导致消费方不可用并将不可用逐渐放大的过程。

根本原因：在调用链路中某一个服务执行业务时间过长，或者是大规模出现异常导致自身服务不可用，并把这种不可用放大的情况。

![image-20211022092746251](./images/image-20211022092746251.png)

### 1.2 服务熔断

熔断器本身是一种开关装置，当某个服务单元发生故障之后，通过断路器（Hystrix）的故障监控，某个异常条件被触发，直接熔断整个服务，想调用方法返回一个符合预期的可处理的备选响应（FallBack）,而不是长时间的等待或者抛出调用方无法处理的异常，就保证了服务调用方的线程不会长时间被占用，避免故障在分布式系统中蔓延，乃至雪崩。如果目标服务情况出现好转则恢复调用，服务熔断是解决服务雪崩的重要手段。

![image-20211022093708868](./images/image-20211022093708868.png)

#### 断路器打开和关闭的条件

```properties
1、当满足一定的阈值的时候（默认10秒内超过20个请求次数）
2、当失败率达到一定的时候（默认10秒内超过50%的请求失败）
3、达到以上阈值，断路器会打开
4、当开启的时候，所有请求都不会进行转发
5、一段时间之后（默认是5s），这个时候断路器是半开状态，会让其中一个请求进行转发，如果成功，断路器会关闭，若失败，继续开启，重复4和5。
```

![image-20211022094624475](./images/image-20211022094624475.png)

### 1.3 服务降级

服务压力剧增的时候，根据当前的业务情况及流量对一些服务和页面有策略的降级，以此环节此服务器的压力，以保证核心任务的进行。同时保证部分甚至大部分任务客户能得到正确的响应，也就是当前扥请求处理不了或者处理出错了，给一个默认的返回。

总结一句话：关闭微服务中某些边缘服务，保证系统核心服务正常运行。

![image-20211022094742980](./images/image-20211022094742980.png)

### 1.4 服务熔断和降级总结

#### 1.4.1 共同点

+ 目的很一致，都是从可用性可靠性着想，为防止系统的整体缓慢甚至崩溃采取的技术手段
+ 最终表现类似，对于两者来说，最终让用户体验到的是某些功能暂时不可达或者不可用
+ 粒度一般都是服务级别的，当然，业界也有不少更细力度的做法，比如做到数据持久层，只允许查询，不允许增删改
+ 自治性要求很高，熔断模式一般都是服务基于策略的自动触发，降级虽说可人工干预，但在微服务架构下，完全靠人工显然不可能，开关预置，配置中心都是必要手段

#### 1.4.2 不同点

+ 触发原因不太一样，服务熔断一般是某个下游服务的故障引起的，服务降级一般是从整体负荷考虑
+ 管理目标的层次不太一样，熔断其实是一个框架级的处理，每个微服务都需要，而降级一般需要对业务有层级之分。

#### 1.4.3 总结

熔断必会触发降级，所以熔断也是降级的一种，区别在于熔断是对调用链路的保护，而降级是对系统过载的一种保护处理。

### 1.5 Hystrix 

Hystrix是一个用于处理分布式系统的延迟和容错的开源库，在分布式系统中，许多依赖不可避免的会调用失败，超时异常等，Hystrix能够保证在一个依赖出现问题的情况下，不会导致整体服务失败，避免级联故障，提供分布式系统的弹性。

## 2、使用

### 2.1 引入依赖

```xml
<!--        springboot-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

<!--        consul-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-consul-discovery</artifactId>
        </dependency>

<!--       健康管理-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

<!--        openfeign-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
            <version>2.2.3.RELEASE</version>
        </dependency>

<!--        hystrix-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
        </dependency>
```

### 2.2 添加注解

```java
@SpringBootApplication //springboot应用
@EnableFeignClients //服务间通信
@EnableDiscoveryClient //服务注册中心
@EnableCircuitBreaker //服务熔断
public class HystrixClientProductApplication {

    public static void main(String[] args) {
        SpringApplication.run(HystrixClientProductApplication.class,args);
    }
}
```

### 2.3 熔断处理

#### 2.3.1 服务端Controller上熔断处理

```java
@RestController
@ResponseBody
@RequestMapping("/product")
public class ProductController {

    @Autowired
    private ProductClient productClient;

    @RequestMapping("/demo")
  	//如果同时配置了错误处理和默认错误处理 那么优先使用错误处理
    @HystrixCommand(fallbackMethod = "demoFailBack",defaultFallback = "defaultFailBack")
    public String demo(@RequestParam("id") Integer id) {
        return "demo ok!!! "+productClient.demo(id);
    }

    //参数一致
    public String demoFailBack(Integer id){
        return "product 服务不小心被熔断了";
    }

  	//参数一致
    public String defaultFailBack(Integer id){
        return "服务异常";
    }
}
```

#### 2.3.2 客户端OpenFeign降级熔断 

```java
@FeignClient(value = "HYSTRIXCLIENTUSER",fallback = ProductClientFailBack.class)
public interface ProductClient {
	
    @RequestMapping("/user/demo")
    String demo(@RequestParam("id") Integer id);

}

@Component
public class ProductClientFailBack implements ProductClient{
    @Override
    public String demo(Integer id) {
        return "不好意思被熔断了";
    }
}
```

### 2.4  Hystrix仪表盘组件

Hystrix DashBoard：用来显示状态信息。监控每一个@HystrixCommond注解创建一组度量，构建一组信息，然后通过图形化方式展示当前方法的状态信息。不过因为里面有些bug，使用体验不好，就不往后面扩展了~