1.  docker build -t demo-8-app .    
### 创建镜像，注意最后的标点符号，跟jar包和Dockerfile一个目录
### docker run -e TZ=Asia/Shanghai --restart=always -v /root/demo8:/root -d -p 44444:33333 demo-8-app  
### 启动容器,定时任务需要指定时区，端口44444为宿主机端口，33333为容器内的端口，路径类推
### docker logs  
### 通过上个命令返回的id，查看镜像

### docker ps -a | grep demo-8-app | awk '{print $1}'| xargs docker stop 
### 停止容器
### docker ps -a | grep demo-8-app | awk '{print $1}'| xargs docker rm 
### 删除容器
### docker images -a | grep demo-8-app | awk '{print $1}'| xargs docker rmi 
### 删除镜像
--------------------------------------------------------------------------------

## Dockerfile内容，创建一个名字为Dockerfile，无扩展名的文件
```
# 使用官方的Java基础镜像
FROM openjdk:8-jre-alpine

# 复制应用程序JAR文件到容器中
COPY demo-0.0.1-SNAPSHOT.jar /demo-0.0.1-SNAPSHOT.jar

# 指定容器启动命令
CMD ["java", "-jar", "/demo-0.0.1-SNAPSHOT.jar"]
```
