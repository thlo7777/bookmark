# rockeMq 配置

## rocketMQ+centos+安装配置
><https://blog.csdn.net/cdnight/article/details/81027829>   
>[RocketMQ快速安装与使用](https://blog.csdn.net/u010391342/article/details/82150062)  
>[跟我学RocketMQ[1-1]之安装RocketMQ](http://wuwenliang.net/2019/01/09/%E8%B7%9F%E6%88%91%E5%AD%A6RocketMQ-1-1-%E4%B9%8B%E5%AE%89%E8%A3%85RocketMQ/)
> ````
> RocketMQ systemd service  mqnamesrv.service
> [Unit]
> Description=rocketmq name server
> After=network-online.target firewalld.service syslog.target network.target remote-fs.target nss-lookup.target
> 
> [Service]
> ExecStart=/usr/local/rocketmq/bin/mqnamesrv
> ExecStop =/usr/local/rocketmq/bin/mqshutdown namesrv
> 
> [Install]
> WantedBy=multi-user.target
>
> ````

> ````
> RocketMQ systemd service  mqbroker.service    
> [Unit]    
> Description=rocketmq Broker   
> After=mqnamesrv.service network-online.target firewalld.service syslog.target network.target remote-fs.target nss-lookup.target
> 
> [Service]     
> ExecStart=/usr/local/rocketmq/bin/mqbroker -n 10.0.36.88:9876     
> ExecStop =/usr/local/rocketmq/bin/mqshutdown broker       
> 
> [Install]     
> WantedBy=multi-user.target
>
> ````

```
创建MQ topic

cd YOUR_ROCKETMQ_HOME

bash bin/mqadmin updateTopic -c DefaultCluster -t string-topic              -n xx.xxx.xxx.xxx:9876
bash bin/mqadmin updateTopic -c DefaultCluster -t order-paid-topic          -n xx.xxx.xxx.xxx:9876
bash bin/mqadmin updateTopic -c DefaultCluster -t message-ext-topic         -n xx.xxx.xxx.xxx:9876
bash bin/mqadmin updateTopic -c DefaultCluster -t spring-transaction-topic  -n xx.xxx.xxx.xxx:9876

$ sh mqadmin topicList –n 10.45.47.168:9876
```

## 解决 rocketmq 连接异常 sendDefaultImpl call timeout
```text
虚机先装了MQ, 又装了 Docker 发现错误
需要指定  localhost 作为 brokerIP  否则 会自动制定到 docker IP
nohup sh /usr/local/rocketmq/bin/mqnamesrv &
nohup sh /usr/local/rocketmq/bin/mqbroker -n localhost:9876  -c /usr/local/rocketmq/conf/broker.properties &
```
## RocketMQ 解决 No route info of this topic 异常步骤
><https://blog.csdn.net/chenaima1314/article/details/79403113>

## RocketMQ部署时遇到的问题
><https://www.jianshu.com/p/bfd6d849f156>

## 跟我学RocketMQ[1-1]之安装RocketMQ
><http://wuwenliang.net/2019/01/09/%E8%B7%9F%E6%88%91%E5%AD%A6RocketMQ-1-1-%E4%B9%8B%E5%AE%89%E8%A3%85RocketMQ/>

## rocket MQ  2 master no slave 配置
```text

Master a:  10.0.32.223  port 9876

$ sudo firewall-cmd --permanent --zone=public --add-port=9876/tcp
$ sudo firewall-cmd --permanent --zone=public --add-port=10909/tcp
$ sudo firewall-cmd --permanent --zone=public --add-port=10911/tcp

cd  cd /usr/local/rocketmq/conf/2m-noslave/
vim broker-a.properties

    brokerClusterName=cluster-mq01
    brokerName=broker-a
    brokerId=0
    deleteWhen=04
    fileReservedTime=48
    brokerRole=ASYNC_MASTER
    flushDiskType=ASYNC_FLUSH

    # thlo added
    namesrvAddr=10.0.32.223:9876;10.0.32.224:9876
    brokerIP1=10.0.32.223


cd ~/mqserver/
cat mqclusterstart.sh

启动 
#!/bin/bash
nohup sh /usr/local/rocketmq/bin/mqnamesrv &
nohup sh /usr/local/rocketmq/bin/mqbroker -c /usr/local/rocketmq/conf/2m-noslave/broker-a.properties &


-------Master b ------
Master b: 10.0.32.224  port 9876

$ sudo firewall-cmd --permanent --zone=public --add-port=9876/tcp
$ sudo firewall-cmd --permanent --zone=public --add-port=10909/tcp
$ sudo firewall-cmd --permanent --zone=public --add-port=10911/tcp

cd  cd /usr/local/rocketmq/conf/2m-noslave/
vim broker-b.properties

    brokerClusterName=cluster-mq01
    brokerName=broker-b
    brokerId=0
    deleteWhen=04
    fileReservedTime=48
    brokerRole=ASYNC_MASTER
    flushDiskType=ASYNC_FLUSH

    # thlo added
    namesrvAddr=10.0.32.223:9876;10.0.32.224:9876
    brokerIP1=10.0.32.224

cd ~/mqserver/
cat mqclusterstart.sh

启动 
#!/bin/bash
nohup sh /usr/local/rocketmq/bin/mqnamesrv &
nohup sh /usr/local/rocketmq/bin/mqbroker -c /usr/local/rocketmq/conf/2m-noslave/broker-a.properties &
```
