### 1、文件读取

```java
模块：http、server、location、if in location

location / {
  sendfile on;//默认off
}
```



### 2、tcp_nopush

```java
模块：http、server、location

location / {
  tcp_nopush on;//默认off
}

sendfile 开启的情况下，提高网络包的传输效率
```



### 3、tcp_nodelay

```java
模块：http、server、location

location / {
  tcp_nodelay on;//默认on
}

keepalive连接下，提高网络包的传输实时性
```



### 4、压缩

```java
模块：http、server、location、if in location

location / {
	gzip on;//默认 off 
}

压缩传输
```



### 5、压缩比

```java
模块：http、server、location

location / {
  gzip_comm_level 1;//默认1
}

压缩比越高，性能消耗越大
```



### 6、压缩协议版本

```java
模块：http、server、location

location / {
  gzip_http_version 1.1|1.1;//默认1.1
}
```



### 7、Nginx扩展压缩模块

```java
http_gzip_static_module - 预读gzip功能
http_gunzip_module - 应用支持gunzip的压缩方式；//这种方式是用于不支持gzip的方式 很少用
```



```xml
server {
    listen       80;
    server_name  static_file.mxn.com;

    #access_log  /var/log/nginx/host.access.log  main;
    sendfile on;

   # location / {
   #     root   /opt/app/code;
   #     index  server.html index.htm;
   #	#sub_filter 'e' 'mxn';
   #	#sub_filter_once off;
   # }

    location ~ .*\.(jpg|jpeg|gif|png)$ {
        #gzip on;
        #gzip_http_version 1.1;
        #gzip_comp_level 2;
        #gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
        root /opt/app/code/images;
    }

    location ~ .*\.(txt|xml)$ {
        #gzip on;
        #gzip_http_version 1.1;
        #gzip_comp_level 1;
        #gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
        root /opt/app/code/doc;
    }

    location ~ ^/download {
       gzip_static on;
       tcp_nopush on;
       root /opt/app/code;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}
```

