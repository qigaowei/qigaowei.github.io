1. 
```shell
curl -fsSL https://test.docker.com/ -o test-docker.sh
 sudo sh test-docker.sh
# 创建目录
sudo mkdir -p /etc/docker
# 写入配置文件
sudo tee /etc/docker/daemon.json <<-'EOF'
{

    "registry-mirrors": [

    "http://cf-workers-docker-io-2cl.pages.dev/",
"http://dockerhub.timeweb.cloud/",
"http://docker.ketches.cn/",
"http://docker.m.daocloud.io/"

    ]

}

EOF
# 重启docker服务
sudo systemctl daemon-reload 
# 等一会再执行
 sudo systemctl restart docker
```
2. 出问题查看日志
```shell
sudo journalctl -u docker.service
```
3. /etc/docker/daemon.json配置文件一定包含http://