## Redis 的运行测试

> 1. 启动 Redis

执行如下命令启动 Redis

```
redis-server redis.conf
```



> 2. 启动成功后，执行如下命令可以进入 Redis 控制台

```
redis-cli
```

![image-20200116110930549](/Users/kennymoon/Library/Application%20Support/typora-user-images/image-20200116110930549.png)



> 3. 关闭 Redis

关闭 Reids 实例有两种方法，一种是在控制台执行 `shutdown`,然后使用`exit`退出。

![image-20200116111150035](/Users/kennymoon/Library/Application%20Support/typora-user-images/image-20200116111150035.png)

或者可以执行以下命令关闭 Redis 实例

> redis-cli shutdown

![image-20200116111305307](/Users/kennymoon/Library/Application%20Support/typora-user-images/image-20200116111305307.png)



