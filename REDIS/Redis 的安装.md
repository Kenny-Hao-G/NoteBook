## Redis 的安装

## Redis 在 Linux 上的安装与部署

> 注：本人是在 CentOS7 操作系统部署，没有系统的小伙伴可以去阿里云购买或者虚拟机自己搭建。

> ### 一、Redis 安装

### 1. 下载 Redis

首先进入你想安装的指定文件夹目录：

**本人安装在 `/usr/local/resources/redis`**

```
cd /usr/local/resources/redis
```



执行如下命令下载 Redis

```
wget http://download.redis.io/releases/redis-5.0.5.tar.gz
```

如果提示没有找到 `wget`命令可以先执行 `yum install wget`安装`wget`



### 2. 安装 Redis

依次执行如下命令，解压下载的文件进入文件夹进行安装：

```
tar -zxvf redis-5.0.5.tar.gz
cd redis-5.0.5
make install
```



### 3. 配置 Redis

> 1. 编辑解压目录下的 **redis.conf** 文件，首先将 **daemonize** 由 **no** 改成 **yes**，表示允许 **Redis** 在后台启动。

```
# 我们进入编辑模式，编辑 redis.conf
sudo vim redis.conf

# 查找 daemonize，将 no 改为 yes
/ daedaemonize

# 按 I 键进入插入模式，将 no 修改为 yes
# 接下来修改其他内容
```

![image-20200116110338729](/Users/kennymoon/Library/Application%20Support/typora-user-images/image-20200116110338729.png)



> 2. 在 **bind 127.0.0.1** 前面添加 **#** 将其注释掉，默认情况下只允许本地连接，注释掉后外网就可以连接 **Redis** 了。

```
# 查找 bind 127.0.0.1
# 修改将其注释掉
```

![image-20200116110422791](/Users/kennymoon/Library/Application%20Support/typora-user-images/image-20200116110422791.png)



> 3. 关闭防火墙

为了能远程连接 Redis，分别输入以下命令关闭 CentOS 防火墙，并禁止防火墙开机启动

```
systemctl stop firewalld.service
systemctl disable firewalld.service
```



## 配置 Redis 外网可访问

由于 redis 采用的安全策略，默认会只准许本地访问。需要通过简单配置，完成允许外网访问。

修改 redis 的配置文件，将所有 bind 信息全部屏蔽。

修改`redis.conf`配置文件，将所有的 bind 注释掉

```
# bind 192.168.1.100 10.0.0.1 
# bind 192.168.1.8 
# bind 127.0.0.1
```

修改完成后，需要重启 Redis 服务

随后修改 Linux 的防火墙，开启你的 Redis 服务端口，默认是 6379

```
-A INPUT -m state –state NEW -m tcp -p tcp –dport 6379 -j ACCEPT 
…… 
-A INPUT -j REJECT –reject-with icmp-host-prohibited
```



