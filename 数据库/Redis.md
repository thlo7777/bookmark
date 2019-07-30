# Redis使用

## 浅谈REDIS数据库的键值设计（转）
><https://www.cnblogs.com/ajianbeyourself/p/4474597.html>

## redis单机版伪分布式集群搭建
><https://blog.csdn.net/u010395496/article/details/79858798>

## Redis 容量评估
><https://blog.csdn.net/u011983531/article/details/79598671>

## redis 安装
1. ### Redis 3.0.7版本启动时出现警告的解决办法  
   <https://blog.csdn.net/jiangshouzhuang/article/details/50864933>  
   <https://www.jianshu.com/p/7ca4b74c92be>
2. ### 

## Redis 列出集群中已知的所有节点（node）,以及这些节点相关 信息
```text
$ ./redis-cli  -h 10.0.32.225 -p 7004
10.0.32.225:7004> cluster nodes
```

## Redis cluster delete pattern
```text
redis-cli -h 10.0.32.225 -p 7005 --scan --pattern metadata*|xargs -L 1 redis-cli -h 10.0.32.225 -p 7005 del
```

## centos6下redis cluster集群部署过程
><https://www.cnblogs.com/kevingrace/p/7846324.html>

### 关闭redis 持久化
```text
redis的持久化——RDB和AOF。redis有两种方式支持持久化，分别是RDB和AOF。

1.注释掉原来的持久化规则

#save 900 1

#save 300 10

#save 60 10000

2.设置为空

save ""

然后重启redis服务即可。

执行操作命令

语法：

CONFIG SET save ""

执行命令后，无需重启服务，即可生效。

3. 默认情况下redis并没有开启AOF，AOF的配置在redis.conf中注释为APPEND ONLY MODE的模块里，如果要开启AOF，需要将appendonly no改为appendonly yes。
在redis_aof.conf配置文件中，appendfsync指定了redis进行aof持久化的时机，有如下三种方式：

appendfsync always：每次收到写命令就立即强制写入磁盘，性能最低，但是最能保证数据的完整性，不推荐使用

appendfsync everysec：每秒钟强制写入磁盘一次，在性能和持久化方面做了很好的折中，推荐

appendfsync no：从不写入，完全依赖os，性能最好，不能保证数据的完整性




```

### [Redis常用命令的时间复杂度整理](http://blog.liukaining.com/redis_o_n.html)
```text
Redis 的命令按照常用的数据结构分为六种类型：

Key
String
Hash
List
Set
SortedSet
本文主要整理以上 6 类的最常使用的命令，全部的命令建议查看上文的文档。
```

### [How fast is Redis?](https://redis.io/topics/benchmarks)
```text
Redis includes the redis-benchmark utility that simulates running commands done by 
N clients at the same time sending M total queries (it is similar to the Apache's ab utility). 
```

### [Redis源码分析](https://blog.csdn.net/Androidlushangderen/column/info/redis-code)
```text
对Redis的源码从结构体开始到主从复制各个原理性的模型进行分析
```