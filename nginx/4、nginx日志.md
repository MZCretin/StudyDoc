### 1、日志类型

error.log  错误信息

access_log  所有的请求信息



### 2、Nginx变量

```java
 log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';
```



+ HTTP请求变量

arg_PARAMETER、http_HEADER、send_http_HEADER

+ Nginx 内置的

去官网查看

+ 自定义变量





