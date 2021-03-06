## Redis 简介

Redis 是完全开源免费的，遵循 BSD 协议，是一个高性能的 KEY-VALUE 数据库。

Redis 与其他的 KEY-VALUE 缓存产品有以下三个特点：

1. Redis 支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载使用。
2. Redis 不仅仅支持简单的 KEY-VALUE 类型的数据，同时还提供 List、Set、ZSet、Hash 等数据结构的存储。
3. Redis 支持数据的备份，即 Master-Slave 模式的数据备份。



## Redis 优势

1. 性能极高，Redis 的读写速度是 110000 次/s，写的速度是 81000 次/s。
2. 丰富的数据类型，Redis 支持二进制案例的 Strings，Lists，Hashes，Sets 及 Ordered Sets 数据类型操作。
3. 原子，Redis 的所有操作都是原子性的，原子性的意思就是要么成功执行，要么失败完全失败不执行。单个操作是原子性的。多个操作也支持事务，即原子性，通过 `MULTI`和`EXEC`指令包起来。
4. 丰富的特性，Redis 还支持 `PUBLISH/SUBSRIBE`,通知 Key 过期等等特性。



## Redis与其他 KEY-VALUE 存储有什么不同？

1. Redis 有着更为复杂的数据结构并且提供对他们的原子性操作，这是一个不同于其他数据库的进化路径。Redis 的数据类型都是基于基本数据结构同时对程序员透明，无需进行额外的抽象。
2. Redis 运行在内存中但是可以持久化到磁盘，所有在对不同数据库进行高速读写的时需要权衡内存，因为数据量不能大于硬件内存。在内存数据库方面的另一个优点是，相比在磁盘上相同的复杂的数据结构，在内存中操作起来非常简单，这样 Redis 可以做很多内存复杂性很强的事情。同时，在磁盘格式方面他们是紧凑的以追加的方式产生的，因为他们并不需要进行随机访问。



## 笔记 📒

## 什么是原子性？什么是原子性操作？

举个例子：

A想要从自己的帐户中转1000块钱到B的帐户里。那个从A开始转帐，到转帐结束的这一个过程，称之为一个事务。在这个事务里，要做如下操作：

1. 从A的帐户中减去1000块钱。如果A的帐户原来有3000块钱，现在就变成2000块钱了。

2. 在B的帐户里加1000块钱。如果B的帐户如果原来有2000块钱，现在则变成3000块钱了。

如果在A的帐户已经减去了1000块钱的时候，忽然发生了意外，比如停电什么的，导致转帐事务意外终止了，而此时B的帐户里还没有增加1000块钱。那么，我们称这个操作失败了，要进行回滚。回滚就是回到事务开始之前的状态，也就是回到A的帐户还没减1000块的状态，B的帐户的原来的状态。此时A的帐户仍然有3000块，B的帐户仍然有2000块。

我们把这种要么一起成功（A帐户成功减少1000，同时B帐户成功增加1000），要么一起失败（A帐户回到原来状态，B帐户也回到原来状态）的操作叫原子性操作。

如果把一个事务可看作是一个程序,它要么完整的被执行,要么完全不执行。这种特性就叫原子性。

## 什么是 Key-Value 存储？

Java 中的 Map 就是以 `Key-Value`存储的。

键唯一，对应一个值，值的形式多样。

比如：

```java
Map<String, Integer> map = new HashMap<String, Integer>();
map.put("Number1", 1);
map.put("Number2", 2);
```

