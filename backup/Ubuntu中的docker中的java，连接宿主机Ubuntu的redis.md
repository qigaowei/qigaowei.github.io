使用 Docker Network 配置
```shell
docker run --network host your-docker-image
```
这种方法使容器能够像宿主机一样访问 127.0.0.1，即容器内的应用可以使用 127.0.0.1 连接 Redis，但这只适用于 Linux 主机。