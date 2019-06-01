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