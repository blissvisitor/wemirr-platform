# 环境安装

安装 Redis （>=3.0）

```shell
docker pull redis:latest
docker run -itd --name redis -p 6379:6379 redis
```

安装 Mysql （>= 5.7）

```shell
docker pull mysql:latest
docker run -itd --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
```

安装 Nacos （>=2.0）

```shell
docker pull nacos/nacos-server
# 创建Nacos容器，注意开放9848及9848，原因：https://nacos.io/en/docs/next/v2/upgrading/2.0.0-compatibility#deployment
docker run -itd --name nacos -p 8848:8848 -p 9848:9848 --restart=always -e MODE=standalone nacos/nacos-server
```

安装 RabbitMQ

```shell
docker pull macintoshplus/rabbitmq-management
docker run -d  -p 5671:5671 -p 5672:5672  -p 15672:15672 -p 15671:15671  -p 25672:25672  macintoshplus/rabbitmq-management
```

文件存储

```shell
docker pull bitnami/minio:latest
# 创建MinIO容器，密码必须大于等于8个字节，否则启动失败；初始化一个默认bucket为wemirr-bucket；9000端口与Gateway冲突，两个端口偏移10000
docker run -itd --name minio -p 19000:9000 -p 19001:9001 -e MINIO_ROOT_USER=minio -e MINIO_ROOT_PASSWORD=minio_pwd -e MINIO_DEFAULT_BUCKETS=wemirr-bucket bitnami/minio:latest
```
