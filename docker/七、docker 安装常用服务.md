## 一、安装 mysql

### 1、安装哪个服务就去docker hub搜索对应的服务镜像

### 2、点击进入该服务的docker hub

### 3、确定使用的版本

docker pull mysql:5.7.32

### 4、如何使用镜像

a、基础启动mysql服务

docker run -e MYSQL_ROOT_PASSWORD=root mysql:5.7.32

-e MYSQL_ROOT_PASSWORD=root 代表给root用户指定密码

b、启动一个musql 服务，后台运行，指定root用户密码 指定容器名称

docker run -d -p 3307:3306 -e MYSQL_ROOT_PASSWORD=root --name mysql mysql:5.7.32

c、启动一个mysql后台运行，指定root用户密码，指定容器名字，使用数据卷将数据持久化到宿主机系统 指定名字

注意：通过dockerhub描述得知mysql存储数据文件目录文件放置在容器中的这个目录：/var/lib/mysql

docker run -d -p 3307:3306 -e MYSQL_ROOT_PASSWORD=root --name mysql -v mysqldata:/var/lib/mysql mysql:5.7.32

d、启动一个mysql服务，后台运行，指定root密码，指定容器名称，使用数据卷进行数据持久化，已修改之后的配置文件启动

docker run -d -p 3308:3306 -e MYSQL_ROOT_PASSWORD=root --name mysql3308 -v mysqldata:/var/lib/mysql -v mysqlconfig:/etc/mysql mysql:5.7.32

## 二、安装 tomcat

### 1、下载tomcat服务

docker pull tomcat:8.0-jre8

### 2、启动tomcat服务

a、启动一个基本tomcat服务

docker run -d -p 8081:8080 --name tomcat tomcat:8.0-jre8

b、将部署应用目录通过数据卷挂在宿主机系统

注意：部署web应用在容器中目录为 /usr/local/tomcat/webapps 配置文件 /usr/local/tomcat/conf

docker run -d -p 8081:8080 --name tomcat -v apps:/usr/local/tomcat/webapps tomcat:8.0-jre8

c、修改配置文件，并将应用目录通过数据卷挂载到宿主机系统

docker run -d -p 8081:8080 --name tomcat -v apps:/var/local/tomcat/webapps -v confs:/usr/local/tomcat/conf tomcat:8.0-jre8

## 三、安装redis

### 1、下载redis镜像

docker pull redis:5.0.10

### 2、启动redis

docker run -d -p 6379:6379 --name redis redis:5.0.10

### 3、开启redis持久化

docker run -p 6379:6379 --name redis -v  redisdata:/data redis:5.0.10 redis-server --appendonly yes

注意：一旦开启持久化之后，持久化生成aof文件会被放入容器中的/data目录中

### 4、修改redis配置文件，以配置文件方式启动

注意：在当前/root/redisconf 目录中存在 redis conf 配置文件

docker run -p 6380:6379 -v /root/redisconf:/usr/local/etc/redis --name myredis -d redis:5.0.10 redis-server /usr/local/etc/redis/redis.conf 