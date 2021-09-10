### 1、nginx官方模块

+ --with-http_stub_status_module

  Nginx的客户端状态

  ```java
  server {
    location /mystatus {
      stub_status; 
    }
  }
  ```

  

+ --with-http_random_index_module

  目录中选择一个随机主页

  注意点：这个里面 .开头的文件不会被随机到

  ```java
  server {
    locatio / {
      root /opt/app/code;
      random_index: on;
    }
  }
  ```

+ --with-http_sub_module

  HTTP内容替换

  ```java
  server {
    root /opt/app/code;
    index index.tml index.htm;
    sub_filter 'server' 'mxn';
    sub_filter_once off; //off全部替换 默认on 仅仅替换第一个
  }
  ```

+ 频率限制

  + 连接频率限制：

    limit_conn_module

    ```java
    limit_conn_zone $binary_remote_addr zone=conn_zone:1m;
    
    location / {
      root /opt/app/code;
      limit_conn conn_zone 1;//一次只能有一个请求
      index index.html;
    }
    ```

  + 请求频率限制：

    limit_req_module

    ```java
    limit_req_zone $binary_reamote_addr zone=req_zone:1m rate=1r/s;
    
    location / {
      root /opt/app/code;
      limit_req zone=req_zone burst=3 nodelay;
      limit_req zone=req_zone burst=3;
      limit_req zone=req_zone;
      index index.html;
    }
    
    zone=one ：设置使用哪个配置区域来做限制，与上面limit_req_zone 里的name对应
    burst=5：重点说明一下这个配置，burst爆发的意思，这个配置的意思是设置一个大小为5的缓冲区当有大量请求（爆发）过来时，超过了访问频次限制的请求可以先放到这个缓冲区内等待，但是这个等待区里的位置只有5个，超过的请求会直接报503的错误然后返回。
    nodelay：如果设置，会在瞬时提供处理(burst + rate)个请求的能力，请求超过（burst + rate）的时候就会直接返回503，永远不存在请求需要等待的情况。（这里的rate的单位是：r/s）如果没有设置，则所有请求会依次等待排队
    
    ```

  + 

+ 访问控制

  + 基于IP的控制访问

    http_access_module

    局限性：对代理ip无法识别

    方法：

    1、采用别的http头信息控制访问，如：HTTP_X_FORWARD_FOR

    2、结合geo模块，一个nginx模块

    3、通过HTTP自定义变量传递

    ```java
    location / {
      root /opt/app/code;
      deny 222.128.189.17;//禁止当前ip访问
      allow all;//其他所有ip可以访问
      index index.html;
    }
    
    location / {
      root /opt/app/code;
      allow 222.128.189.17/24;//仅仅当前ip段可以访问
      deny all;//禁止其他访问
      index index.html;
    }
    ```

    

  + 基于用户的信任登陆

    http_auth_basic_module

    ```java
    首先创建一个账号
    htpasswd -c ./auth_conf cretin 然后会要求你输入密码
      
    location /test_auth.html {
      root /opt/app/code;
      auth_basic "Auth access test!input your password";
      auth_basic_user_file /etc/nginx/auth_conf;
    }
    ```

    局限性：

    1、用户信息依赖文件方式，效率低下

    2、操作管理比较机械，效率低下

    解决方案：

    1、Nginx 结合 LUA

    2、Nginx和LDAP打通，利用nginx-auth-ldap模块

### 2、第三方模块

