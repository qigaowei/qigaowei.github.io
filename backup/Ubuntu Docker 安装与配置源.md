```shell
 curl -fsSL https://test.docker.com -o test-docker.sh
 sudo sh test-docker.sh
```

```shell
# 创建目录

sudo mkdir -p /etc/docker


# 写入配置文件

sudo tee /etc/docker/daemon.json <<-'EOF'

{

    "registry-mirrors": [

    	"https://改成自己的.mirror.aliyuncs.com"

    ]

}

EOF

# 重启docker服务

sudo systemctl daemon-reload && sudo systemctl restart docker
```

