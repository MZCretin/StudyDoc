### 1、安装基础库

```java
安装基础库
yum -y install gcc gcc-c++ autoconf pcre pcre-devel make automake
安装基本的工具
yum -y install wget httpd-tools vim
```



### 2、初始化一些需要的目录

```java
cd /opt;
mkdir app download logs work backup
```



### 3、检查yum源是否可以可用

```java
yum list|grep gcc
```



### 4、关闭iptables

```java
iptables -L //检查有没有规则
iptables -F //关闭iptables规则
iptables -t nat -L //检查有没有规则
iptables -t nat -F //关闭iptables规则
```



### 5、关闭SELinux

```java
getenforce //查看状态
setenforce 0 //关闭SELinux
```



### 6、安装nginx

```java
1、进入nginx官方网站：nginx.org 
2、点击download
3、按照文档安装
  1、sudo yum install yum-utils
  2、新建 /etc/yum.repos.d/nginx.repo
  3、输入以下内容
    [nginx-stable]
    name=nginx stable repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=1
    enabled=1
    gpgkey=https://nginx.org/keys/nginx_signing.key
    module_hotfixes=true

    [nginx-mainline]
    name=nginx mainline repo
    baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
    gpgcheck=1
    enabled=0
    gpgkey=https://nginx.org/keys/nginx_signing.key
    module_hotfixes=true
  4、sudo yum install nginx
4、安装完成之后 nginx -v 查看版本号
5、nginx -V 查看编译参数
```

