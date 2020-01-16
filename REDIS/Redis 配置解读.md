## Redis 配置解读

> 简介

若想修改 Redis 的一些默认配置，需要在`redis.conf`的配置文件内修改对应的内容。



## 参数说明

> daemonize no

redis 默认不是以守护进程的方式运行，可以通过该配置项修改，使用 yes 启动守护进程



> port 6379 

指定 Redis 监听端口，默认端口为 6379



> bind 127.0.0.1

绑定的主机地址，如果注释掉则外网所有 IP 都可进行访问



> timeout 300

当客户端闲置多长时间后关闭连接，结果指定为0，表示关闭该功能



> loglevel notice 

指定日志记录级别，redis 总共支持四个级别：debug、verbose、notice、warning，默认为 notice



> logfile stdout 

日志记录方式，默认为标准输出，如果配置 Redis 为守护进程方式运行，而这里又配置为日志记录方式为标准输出，则日志将会发送给 /dev/null



> database 16

设置数据库的数量，默认数据库为 0，可以使用 SELECT命令在连接上指定数据库 ID



> save <seconds> <changes> 
>
> Redis 默认配置文件中提供了三个条件：
>
> save 900 1 
>
> save 300 10
>
> save 60 10000
>
> 分别表示 900 秒（15 分钟）内有一个更改，300 秒（5 分钟）有 10 个更改，（60 秒）有 10000 个更改

指定多长时间内，有多少次更新操作，就将数据库同步到数据文件，可以过个条件配合。







