```shell
docker pull mysql:5.7
# docker pull mysql:8

mkdir -p /data/mysql/log
mkdir -p /data/mysql/data
mkdir -p /data/mysql/conf.d
echo "" > /data/mysql/my.cnf

ls -la /data/mysql

docker run --name mysql \
--restart=always \
-p 3306:3306 \
-v /data/mysql/log:/var/log/mysql \
-v /data/mysql/data:/var/lib/mysql \
-v /data/mysql/conf.d:/etc/mysql/conf.d \
-v /data/mysql/my.cnf:/etc/my.cnf \
-e MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD} \
-d mysql:5.7

```

- 在宿主机中执行 mysql 容器 的 命令
```shell
docker exec -it mysql bash
> mysql -uroot -p${MYSQL_ROOT_PASSWORD} --port=3306 -h127.0.0.1 -e 'show databases;'
> exit

```

参考https://www.cnblogs.com/johnnyzen/p/18077425