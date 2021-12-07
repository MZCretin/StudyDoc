# Docker安装

通用脚本安装方式：

### 1、安装docker

curl -fsSL get.docker.com -o get-docker.sh

sudo sh get-docker.sh --mirror Aliyun

### 2、启动服务

systemctl status |start |stop |restart docker

### 3、检测docker启动成功

docker info 查看安装docker 引擎号版本

### 4、配置docker开机自启动

systemctl enable docker

### 5、建立docker组 并使用root用户

sudo groupadd docker

sudo usermod -aG docker $USER

### 6、重启docker服务

systemctl restart docker

### 7、docker引擎和帮助命令

docker info ：里面有server和client，它是个cs架构。

docker执行命令格式（输入docker查看）：

docker [options(可以省略)] command (具体命令不可省略)

### 8、镜像加速

您可以通过修改daemon配置文件/etc/docker/daemon.json来使用加速器

```java
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://7xy60x72.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```





