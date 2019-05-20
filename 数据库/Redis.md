# Redis使用

## 浅谈REDIS数据库的键值设计（转）
><https://www.cnblogs.com/ajianbeyourself/p/4474597.html>

## redis单机版伪分布式集群搭建
><https://blog.csdn.net/u010395496/article/details/79858798>

## Redis 容量评估
><https://blog.csdn.net/u011983531/article/details/79598671>

## Redis 列出集群中已知的所有节点（node）,以及这些节点相关 信息
```text
127.0.0.1:7001>cluster nodes
```

## Redis cluster delete pattern
```text
redis-cli -h 10.0.32.225 -p 7005 --scan --pattern metadata*|xargs -L 1 redis-cli -h 10.0.32.225 -p 7005 del
```