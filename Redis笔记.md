--- 
title: Redis笔记
date: 2019-9-1 00:00:00
tags:
- Redis
- notes
---
--------------------------
### Redis 数据结构 
* string
* list
* hash
* zset
* set
* geo
### Redis 持久化机制
RDB 可以定时备份内存中的数据集。服务器启动的时候，可以从 RDB 文件中恢复数据集。
![](https://i.loli.net/2019/10/03/jwqfMpXG3k7Hmly.png)
Redis 支持两种方式进行 RDB 持久化：当前进程执行和后台执行（BGSAVE）。RDB BGSAVE 策略是 fork
出一个子进程，把内存中的数据集整个 dump 到硬盘上。两个场景举例：
  1. Redis 服务器初始化过程中，设定了定时事件，每隔一段时间就会触发持久化操作；进入定时事件处理程序中，就会 fork 产生子进程执行持久化操作。
  2. Redis 服务器预设了 save 指令，客户端可要求服务器进程中断服务，执行持久化操作。

AOF(append only file) 可以记录服务器的所有写操作。在服务器重新启动的时候，会把所有的写操作重新执行一遍，从而实现数据备份。当写操作集过大（比原有的数据集还大），Redis 会重写写操作集。
redis AOF 有后台执行和边服务边备份两种方式。
![](https://i.loli.net/2019/10/03/gT67WsfAlFohK49.png)
  1. fork 一个子进程，主进程仍进行服务，子进程执行AOF 持久化，数据被dump 到磁盘上。与 RDB 不同的是，后台子进程持久化过程中，主进程会记录期间的所有数据变更（主进程还在服务），并存储在 server.aof_rewrite_buf_blocks 中；后台子进程结束后,Redis 更新缓存追加到 AOF 文件中，是 RDB 持久化所不具备的
  2. 边服务边备份的方式，即 Redis 服务器会把所有的数据变更存储在 server.aof_buf 中，并在特定时机将更新缓存写入预设定的文件（server.aof_filename）。特定时机有三种：
     1. 进入事件循环之前
     2. Redis 服务器定时程序 serverCron() 中
     3. 停止 AOF 策略的 stopAppendOnly() 中
### Redis 的一致性哈希算法
分段成环...
详细：[链接](https://crossoverjie.top/2018/01/08/Consistent-Hash/)
### 当散列类型的value值非常大的时候怎么进行压缩
emmm这玩意本来就是内存换时间吧。
1、过滤不必要的数据。eg:缓存一个用户的信息，只需缓存基本信息即可。不必要的信息过滤掉。
2、精简数据。角色类型：svip 1=>1代替。
3、数据压缩。存进 redis 之前我们还可以对内容进行压缩，常用的工具有 GZIP、Snappy。
### redis 怎么实现摇一摇与附近的人功能(GEO)
主要使用GEO库实现，排序，查找.
* 摇一摇
  1. 随机获取 
* 附近的人
  1. 分块
  2. 前缀和
参考:[链接](https://www.httproot.com/article/23)
### redis 主从复制过程

### Redis 如何解决 key 冲突
和HashMap原理一样，使用链地址法，在hash冲突的情况下在节点后面以next节点的形式追加...
### redis 是怎么存储数据的
k-v，key只能为String类型。
### redis 使用场景
* 高性能适合当做缓存可以和memcache比较。
* 丰富的数据结构，可以方便的求并集（共同好友），热度自排序等。
* 自动过期，短信验证码、具有时间性的商品展示等。
* 并发比较高的场景，秒杀等。