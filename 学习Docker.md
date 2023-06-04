# 学习Docker

首先安装

1.如果你有旧版的

````
apt-get remove docker docker-engine docker.io containerd runc
````

2.如果你没有旧版，要安装新版的

````
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
````

3.安装证书

````
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
````

4.写入软件源信息

````
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
````

5.安装

````
sudo apt-get install docker-ce docker-ce-cli containerd.io
````

中途出现问题 可以sudo apt-get update





6.启动docker

````
systemctl start docker
````

7.安装docker工具

````
apt-get -y install apt-transport-https ca-certificates curl software-properties-common
````

8.重启docker

````
service docker restart
````

9.测试是否成功，输入sudo docker run hello-world 

去远程docker库扒hello-world

![img](https://img-blog.csdnimg.cn/e565b488ed0e4e5d817f546711da4e3a.png)

10.查看docker版本

````
sudo docker version
````

参考网址

````
https://blog.csdn.net/u012563853/article/details/125295985?ops_request_misc=&request_id=&biz_id=102&utm_term=Ubutun%E5%AE%89%E8%A3%85docker&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-125295985.142^v88^insert_down28v1,239^v2^insert_chatgpt&spm=1018.2226.3001.4187
````





# 使用Docker安装Redis

Redis官网[Download | Redis](https://redis.io/download/)

一、

docker search <镜像名称> 

````
命令：docker search redis:后面接版本号 不写默认latest
````

二、Docker拉取镜像

````
docker pull redis
````

三、Docker挂载配置文件

````
1）、挂载 redis 的配置文件
本人配置的redis.conf的路径为 /home/redis/myredis/myredis.conf
2）、挂载 redis 的持久化文件（为了数据的持久化）。
持久数据目录 /home/redis/myredis/date
````

这里本人注意到的问题。就是用户切换才能改

![image-20230604204253452](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604204253452.png)

这里是phgg ，我们需要root才能去修改文件 

切换用户路径 : 

````
sudo su - 切换用户
````

phgg->root

![image-20230604204433093](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604204433093.png)

![image-20230604204512197](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604204512197.png)

ok 下一步

为了更方便使用编辑器 安装个sudo apt install vim 这样方便写一下

Esc 关闭模式   i inserct 插入模式   

:w 保存  :q退出   就这几个够用了吧

配置文件

> # bind 192.168.1.100 10.0.0.1
> # bind 127.0.0.1 ::1
>
> # bind 0.0.0.0  

> protected-mode no
> port 6379
> tcp-backlog 511
> requirepass 000415
> timeout 0
> tcp-keepalive 300
> daemonize no
> supervised no
> pidfile /var/run/redis_6379.pid
> loglevel notice
> logfile ""
> databases 30
> always-show-logo yes
> save 900 1
> save 300 10
> save 60 10000
> stop-writes-on-bgsave-error yes
> rdbcompression yes
> rdbchecksum yes
> dbfilename dump.rdb
> dir ./
> replica-serve-stale-data yes
> replica-read-only yes
> repl-diskless-sync no
> repl-disable-tcp-nodelay no
> replica-priority 100
> lazyfree-lazy-eviction no
> lazyfree-lazy-expire no
> lazyfree-lazy-server-del no
> replica-lazy-flush no
> appendonly yes
> appendfilename "appendonly.aof"
> no-appendfsync-on-rewrite no
> auto-aof-rewrite-percentage 100
> auto-aof-rewrite-min-size 64mb
> aof-load-truncated yes
> aof-use-rdb-preamble yes
> lua-time-limit 5000
> slowlog-max-len 128
> notify-keyspace-events ""
> hash-max-ziplist-entries 512
> hash-max-ziplist-value 64
> list-max-ziplist-size -2
> list-compress-depth 0
> set-max-intset-entries 512
> zset-max-ziplist-entries 128
> zset-max-ziplist-value 64
> hll-sparse-max-bytes 3000
> stream-node-max-bytes 4096
> stream-node-max-entries 100
> activerehashing yes
> hz 10
> dynamic-hz yes
> aof-rewrite-incremental-fsync yes
> rdb-save-incremental-fsync yes



启动

> docker run --restart=always --log-opt max-size=100m --log-opt max-file=2 -p 6379:6379 --name myredis -v /home/redis/myredis/myredis.conf:/etc/redis/redis.conf -v /home/redis/myredis/data:/data -d redis redis-server /etc/redis/redis.conf  --appendonly yes  --requirepass 000415

![image-20230604210730827](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604210730827.png)

成功界面

![在这里插入图片描述](https://img-blog.csdnimg.cn/f2c7c58a3f1740c2b1d0a750f671f6eb.png#pic_center)



测试

1.查看启动模式

```
docker ps -a |grep myredis # 通过docker ps指令查看启动状态，是否成功.
```

2、查看容器运行日志

```
命令：docker logs --since 30m <容器名>
docker logs --since 30m myredis
```

3.还可以通过docker ps -a

![image-20230604211332730](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604211332730.png)

查看Name

![image-20230604211556768](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604211556768.png)

docker

![image-20230604211658248](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604211658248.png)

安装启动工作

docker images 查看镜像

![image-20230604212227456](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604212227456.png)

dockers ps 查看进程

启动成功

![image-20230604212019779](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604212019779.png)



停止redis



查看命令

![image-20230604211837288](C:\Users\14399\AppData\Roaming\Typora\typora-user-images\image-20230604211837288.png)

没有redis-cli那就安装一下工具