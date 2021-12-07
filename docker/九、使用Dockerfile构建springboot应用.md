## 一、开发一个完整的springboot应用

开发需求

## 二、对项目进行打包

生成一个jar包

## 三、在服务器中创建上下文目录

### a、mkdir project_dir

### b、在project_dir目录中 touch Dockerfile

### c、上传jar包到project_dir文件

### d、编写Dockerfile

```dockerfile
FROM openjdk:8-jre
WORKDIR /app #创建一个默认会进入的工作目录 希望把后面的jar包放在里面 
ADD domo-0.0.1-SNAPSHOT.jar app.jar  #使用add 是因为想把jar包重命名一下 
EXPOSE 8081 # 暴露当前项目的端口  
ENTRYPOINT ["java","-jar"] # 确定执行的命令
CMD ["app.jar"] # 指定命令执行的参数 后面这个参数也可以被覆盖  
```

### e、构建一个新的镜像

```shell
docker build -t demo:01 . 
```

### f、运行容器

```shell
docker run -d -p 8081:8081 --name demo demo:01
```

### g、验证

浏览器打开 ： http://127.0.0.1:8081/test/test



