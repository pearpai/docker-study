# docker-study

次项目为docker redis 集群demo，本人机器为mac，如果系统不一致的请自行解决相关问题。如果有什么问题也可以与我沟通联系方式：469901870@qq.com
***
## 本地安装
- docker
- docker-compose

## redis 配置文件修改
```bash
bind 0.0.0.0
daemonize    yes                          //redis后台运行
cluster-enabled  yes                      //开启集群  把注释#去掉
cluster-node-timeout  15000               //请求超时  默认15秒，可自行设置
appendonly  yes                           //aof日志开启  有需要就开启，它会每次写操作都记录一条日志　
dir /data/
logfile /var/log/redis/redis.log
```

## 建立基础 centos
**执行命令：** docker-compose build
此命令为将执行 docker-compose.yml 文件中配置建立基础镜像

## 启动镜像

```bash
docker-compose -f redis.yml up redis_server1 &
docker-compose -f redis.yml up redis_server2 &
docker-compose -f redis.yml up redis_server3 &
docker-compose -f redis.yml up redis_server4 &
docker-compose -f redis.yml up redis_server5 &
docker-compose -f redis.yml up redis_master &


docker exec -it redis_master /bin/sh
redis-trib.rb  create  --replicas  1 172.21.0.7:6379 172.21.0.2:6379 172.21.0.3:6379 172.21.0.4:6379 172.21.0.5:6379 172.21.0.6:6379
```

## 目前这个功能存在一些问题
 - 需要进入容器中启动集群功能
 - 容器id不固定导致问nodes.conf会出现问题 如果有问题 请删除重新启动 后期将进行优化


**如果对优化有兴趣，可以进入下面页面，欢迎沟通交流**
[Redis Linux 优化](http://pearpai.com/2017/06/23/Redis-Linux-optimize/)