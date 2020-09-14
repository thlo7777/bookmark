# mysql如何保证数据一致性
http://blog.51cto.com/xxr007/1965600
# 数据库同步过程中一致性和完整性的保证
https://yq.aliyun.com/articles/135359
# innodb 保证数据一致性
http://pb-water.iteye.com/blog/2232951
# Patterns for distributed transactions within a microservices architecture
https://developers.redhat.com/blog/2018/10/01/patterns-for-distributed-transactions-within-a-microservices-architecture/
# Distributed Transactions and Two-Phase Commit
https://www.endpoint.com/blog/2010/07/29/distributed-transactions-and-two-phase

## 分布式秒杀系统
><https://gitee.com/52itstyle/spring-boot-seckill>

### [What is MySQL Master-Master Replication?](https://www.linode.com/docs/databases/mysql/configure-master-master-mysql-database-replication/)
```text
MySQL Master-Master replication adds speed and redundancy for active websites. With replication, two separate MySQL servers act as a cluster. 
Database clustering is particularly useful for high availability website configurations. Use two separate Linodes to configure database replication, 
each with private IPv4 addresses.
```


```text

#将master_log_file的值替换为在DB1中执行"show master status"显示的File的值，将master_log_pos的值替换为Position的值
change master to master_host='10.0.32.223',master_port=3306,master_user='canal', master_password='123456',master_log_file='mysql-bin.000001',master_log_pos=777;
change master to master_host='10.0.32.224',master_port=3306,master_user='canal', master_password='123456',master_log_file='mysql-bin.000001',master_log_pos=777;
```


### [mysql主主互备模式架构](https://www.kapyan.top/posts/1683246444.html)
```text
DB1和DB2互为主从，保证两台数据库始终是同步的，同时在DB1和DB2上还需要安装高可用软件Keepalived。正常情况下，web server主机仅从BD1进行数据的读、写操作，DB2只负责从DB1同步数据。而Keepalived维护着一个VIP,
此ip用来对外提供连接服务，同时，Keepalived还负责监控DB1和DB2上mysql数据库的运行状态，当DB1主机出现故障或mysql运行异常时，自动将VIP地址和mysql服务切换到DB2上，此时web server主机继续从DB2进行数据的读、写操作。
通过Keepalived保持了数据库服务的连续性，整个切换过程非常快，并且对前端web server主机是透明的。这种方式可以实现95.000%的SLA（服务水平协定）。
```

```text
$ mysql -uroot -p
命令行修改用户密码
alert user  canal identity by '123456';

```

### [MySQL5.7多主一从（多源复制）同步配置](https://my.oschina.net/u/2399373/blog/2878650)
```text
多主一从，也称为多源复制，数据流向：

主库1 -> 从库s
主库2 -> 从库s
主库n -> 从库s
数据汇总，可将多个主数据库同步汇总到一个从数据库中，方便数据统计分析。
读写分离，从库只用于查询，提高数据库整体性能。

```
### [mysql 多主多从配置，自增id解决方案](https://www.cnblogs.com/cocoliu/p/9020845.html)
```text
Master mysql:
server-id=145
log-bin=mysql-bin
auto-increment-increment=2
auto-increment-offset=1
log-slave-updates

给大家一个设置的方法：
auto-increment-increment = 10
auto-increment-offset   = 1
auto-increment-increment = 10
auto-increment-offset   = 2
auto-increment-increment = 10
auto-increment-offset   = 3
这样是不是就可以设置10台主mysql了呢？
```

### [MySQL 5.7: 使用MySQL Router实现应用程序的高可用](https://segmentfault.com/a/1190000011970688)

### [sql update操作数据更新成功，返回的影响行数是0](https://blog.csdn.net/win7system/article/details/73658270)
```text
下面的两种情况均返回0：
       1、没有找到需要更新的数据
        比如，我们进行update的时候，条件是id=5，但是id=5的数据不存在。这种情况下，更新是失败的，返回0，很正确；
       2、要更新的数据和更新的值是完全一样的
        比如，我们要对id=5的记录进行更新，把title变成hello。虽然这条记录存在，但是这条记录的title本来就是hello，
        那么，返回值也是0；
```

### [数据库结构设计（逻辑设计和物理设计）](https://blog.csdn.net/Richard_666/article/details/84099658)
```
需求分析：全面了解产品设计的存储需求

逻辑设计：设计数据的逻辑存储结构

物理设计：根据所用的数据库特点进行表结构设计
```

### [数据库设计之概念结构设计---------E-R图详解](https://blog.csdn.net/zxq1138634642/article/details/9121363)
```
采用E-R方法进行数据库概念设计，可以分成3步进行：首先设计局部E-R模式，然后把各局部E-R模式综合成一个全局的E-R模式，
最后对全局E-R模式进行优化，得到最终的E-R模式，即概念模式。
```

### [E-R图的基本概念（一）](https://blog.csdn.net/chenpidaxia/article/details/62073162)
```
实体-联系方法（Entity-Relationship Approach），也叫E-R模型，由一位叫P.P.S.Chen的大佬最先提出。主要是用来描述现实世界的概念模型。
具体来说就是用一下三种东西来描述我们的问题构成的世界 
```
### [数据库的设计（E-R图，数据库模型图，三大范式）](https://blog.csdn.net/qq_36513534/article/details/82219977)
```
一.数据库设计的概念

数据库设计是将数据库中的数据实体及这些数据实体之间的关系,进行规划和结构化的过程.

二.数据库设计的重要性
```
### [MySQL 分库分表方案，总结的非常好！](https://juejin.im/entry/5b5eb7f2e51d4519700f7d3c)
```
刚开始我们只用单机数据库就够了，随后面对越来越多的请求，我们将数据库的写操作和读操作进行分离， 使用多个从库副本（Slaver Replication）负责读，使用主库（Master）负责写， 从库从主库同步更新数据，保持数据一致。架构上就是数据库主从同步。 从库可以水平扩展，所以更多的读请求不成问题。

但是当用户量级上来后，写请求越来越多，该怎么办？加一个Master是不能解决问题的， 因为数据要保存一致性，写操作需要2个master之间同步，相当于是重复了，而且更加复杂。

这时就需要用到分库分表（sharding），对写操作进行切分。
```

```
不要迷信数据库性能，不要迷信三范式，不要使用外键，不要使用byte，不要使用自增id，不要使用存储过程，不要使用内部函数，
不要使用非标准sql，存储系统只做存储系统的事。当出现系统性能时，如此设计的数据库可以更好的实现迁移数据库
（如mysql->oracle)，实现nosql改造（(mongodb/hadoop），实现key-value缓存(redis,memcache)。
```

### [依赖zookeeper组件的一种高可用实践](https://blog.csdn.net/yu280265067/article/details/62041465)
```
电子商务系统大量使用mysql数据库作为其交易和存储的系统； 随着商户和用户量的不断增长，mysql中存储的数据量会越来越大，
这时把所有数据存储在一张表或者一个数据库中会极大的影响系统的性能和安全。 分库分表是业界一个比较通用的方案，并且也
比较成熟。
为了进行分库分表，我们需要为业务表中设置一个唯一的id；举个商品中心的例子：为了把一个租户下的所有菜品，菜价，菜品分类
放在一下，会在所有这些表上加上一个全局唯一的租户id。
```

### [分布式唯一id：snowflake算法思考](https://juejin.im/post/5a7f9176f265da4e721c73a8)
```
为什么会突然谈到分布式唯一id呢？原因是最近在准备使用RocketMQ，看看官网介绍
```

### [基于Snowflake的分布式唯一ID生成器](https://blog.csdn.net/javaboy/article/details/81978286)
```
先上我的实现的项目地址：https://github.com/johnhuang-cn/snowflake-uid
另外补充解释下，为啥要用这么多位数用于避免worker id重复，实际部署的系统一般也就几百几千台机器/虚拟机，直接为不同的应用
指定不同的id不就完了吗？这主要是考虑在Spring Cloud或者k8s这样的环境里，每个应用是有可能同时开好几个实例的，如果worker
 id是硬编码或者固定配置的，那所有相同应用的实例都会是相同的worker id，肯定会造成UID冲突的。所以就需要有一个渠道能得到
 唯一的id。
```

### [在 Java 中利用 redis 实现分布式全局唯一标识服务](https://juejin.im/post/5a4984265188252b145b643e)
```
根据 redis 的官网的  INCR 命令介绍，它是一个原子操作，效果是是将 redis 数据库中 key 的值加一并且返回这个结果。
如果 key 不存在，将在执行加一操作前，将这个 key 的值设置为0，也就是说执行这个命令的结果是从 1 开始一直累加下去的。
```

### [MySql 索引优化原则](https://blog.csdn.net/yhl_jxy/article/details/88636685?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159745725719195264520265%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=159745725719195264520265&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v3~pc_rank_v4-1-88636685.first_rank_ecpm_v3_pc_rank_v4&utm_term=mysql++%E7%B4%A2%E5%BC%95+%E4%BC%98%E5%8C%96)

### [Mysql索引优化及面试题](https://blog.csdn.net/qq_44590469/article/details/96473238?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159745725719195264520265%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=159745725719195264520265&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v3~pc_rank_v4-2-96473238.first_rank_ecpm_v3_pc_rank_v4&utm_term=mysql++%E7%B4%A2%E5%BC%95+%E4%BC%98%E5%8C%96&spm=1018.2118.3001.4187)

### [MySQL——7种JOIN的sql语法](https://blog.csdn.net/Doit_kang/article/details/84797499?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-4.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-4.channel_param)

#### [mysql中大数据表alter增加字段报错："1034 Incorrect key file for table 'table_name'; try to repair it"](https://www.cnblogs.com/kcxg/p/10912766.html)