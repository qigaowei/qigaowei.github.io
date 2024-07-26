### docker ps -a | grep demo-8-app | awk '{print $1}'| xargs docker stop 停止容器
### docker ps -a | grep demo-8-app | awk '{print $1}'| xargs docker rm 删除容器
### docker images -a | grep demo-8-app | awk '{print $1}'| xargs docker rmi 删除镜像
### docker build -t demo-8-app .    创建镜像，注意最后的标点符号
### docker run -e TZ=Asia/Shanghai --restart=always -v /root/demo8:/root -d -p 44444:33333 demo-8-app  启动容器
### docker logs  通过上个命令的id，查看镜像