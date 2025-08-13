如果宿主机没有指定目录，命令1不会报错，命令2会报错。但是命令1，也达不到想要的效果
1. 命令1
```shell
-v /root/111/tv/config:/iptv-api-lite/config -v /root/111/tv:/iptv-api-lite/output
```
2. 命令2
```shell
 --mount type=bind,source=/root/111/tv,target=/iptv-api-lite/output \
  --mount type=bind,source=/root/111/tv/config,target=/iptv-api-lite/config \
```