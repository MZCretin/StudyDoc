# Docker安装

通用脚本安装方式：

### 1、安装docker

curl -fsSL get.docker.com -o get-docker.sh

sudo sh get-docker.sh --mirror Aliyun

### 2、启动服务

Systemctl status |start |stop |restart docker

### 3、检测docker启动成功

docker info 查看安装docker 引擎号版本

### 4、配置docker开机自启动

systemctl enable docker

### 5、建立docker组 并使用root用户

sudo groupadd docker

Sudo usermod -aG docker $USER

### 6、重启docker服务

systemctl restart docker

