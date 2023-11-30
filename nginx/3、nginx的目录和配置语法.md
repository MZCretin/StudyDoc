### `1、配置目录

```java
/etc/nginx/nginx.conf
/etc/nginx/default.d/*.conf
```



### 2、Nginx的默认语法

| user             | 设置nginx服务端额系统使用用户 |
| ---------------- | ----------------------------- |
| worker_processes | 工作进程数                    |
| error_log        | nginx的错误日志               |
| pid              | nginx服务启动时候的pid        |

| event | worker_connections | 每个进程允许的最大连接数 |
| ----- | ------------------ | ------------------------ |
|       | use                | 工作进程数               |



### 3、server核心配置语法



 

### 4、虚拟主机配置

在同一个nginx上运行多套单独服务，这些服务是相互独立的。

#### 方式一、基于主机多IP的方式

单网卡多IP方式和多网卡多IP方式。

+ 单网卡多IP方式

  ```java
  ip a //查看当前网卡信息
  1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
      inet 127.0.0.1/8 scope host lo
         valid_lft forever preferred_lft forever
      inet6 ::1/128 scope host 
         valid_lft forever preferred_lft forever
  2: eno16777736: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
      link/ether 00:0c:29:2f:6f:03 brd ff:ff:ff:ff:ff:ff
      inet 192.168.17.128/24 brd 192.168.17.255 scope global dynamic eno16777736
         valid_lft 1528sec preferred_lft 1528sec
      inet6 fe80::20c:29ff:fe2f:6f03/64 scope link 
         valid_lft forever preferred_lft forever
  当前ip地址为：192.168.17.128
  先使用ping 找到一个本地没有被使用的ip地址 
  ping 192.168.17.121
  PING 192.168.17.129 (192.168.17.129) 56(84) bytes of data.
  From 192.168.17.128 icmp_seq=1 Destination Host Unreachable
  From 192.168.17.128 icmp_seq=2 Destination Host Unreachable
  From 192.168.17.128 icmp_seq=3 Destination Host Unreachable
  From 192.168.17.128 icmp_seq=4 Destination Host Unreachable
  添加一个ip地址：
  ip a add 192.168.17.121/24 dev eno16777736
  再使用ip a查看网卡信息 ip a
  1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
      inet 127.0.0.1/8 scope host lo
         valid_lft forever preferred_lft forever
      inet6 ::1/128 scope host 
         valid_lft forever preferred_lft forever
  2: eno16777736: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
      link/ether 00:0c:29:2f:6f:03 brd ff:ff:ff:ff:ff:ff
      inet 192.168.17.128/24 brd 192.168.17.255 scope global dynamic eno16777736
         valid_lft 1302sec preferred_lft 1302sec
      inet 192.168.17.121/24 scope global secondary eno16777736
         valid_lft forever preferred_lft forever
      inet6 fe80::20c:29ff:fe2f:6f03/64 scope link 
         valid_lft forever preferred_lft forever
  ```

#### 方式二、基于端口的配置方式

centos 7 使用 ss -luntp 查看当前所有端口号的占用情况

centos 6 使用 netstat -luntp 查看当前所有端口号的占用情况

我们要避开已经被占用的端口

./nginx -s stop -c /etc/nginx/nginx.conf

#### 方式三、基于多个host名称方式（多域名方式）

```java
修改本机的host信息
sudo vim /etc/host
192.128.17.128 1.mxn.com
192.128.17.128 2.mxn.com
保存之后
ping 1.mxn.com 成功即可
ping 2.mxn.com 成功即可
修改conf下server_name 为 1.mxn.com 和 2.mxn.com
server {
    listen       80;
    server_name  1.mxn.com;
		...
}
server {
    listen       80;
    server_name  2.mxn.com;
		...
}
```



