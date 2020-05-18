# canal 配置和同步

### [canal Home](https://github.com/alibaba/canal/wiki)

### [Canal Kafka RocketMQ QuickStart](https://github.com/alibaba/canal/wiki/Canal-Kafka-RocketMQ-QuickStart)
```text
canal 1.1.1版本之后, 默认支持将canal server接收到的binlog数据直接投递到MQ, 目前默认支持的MQ系统有:

kafka: https://github.com/apache/kafka
RocketMQ : https://github.com/apache/rocketmq

Kafka 单机使用案例（本地开发、服务器运行皆可用）: https://juejin.im/post/5dce70ef5188254c74033160

```

### exception.PositionNotFoundException: can't find start position for example
```text
开发环境，如果在canal.properties使用file-instace.xml配置，则重置position下拉取最新位置就可以了
命令：rm conf/{你的实例名}/meta.dat
删除  meta.dat

stop.sh
startup.sh

```


### 多实例配置
```text
$cd conf/
vim canal.properties

    #################################################
    #########               destinations            ############# 
    #################################################
    canal.destinations = example,example1


mdir conf/example   conf/example1

vim  conf/example/instance.properties
    canal.instance.master.address=10.0.32.223:3306

vim  conf/example1/instance.properties
    canal.instance.master.address=10.0.32.224:3306

```


###  parser alter user error
```text
2019-05-27 21:31:29.333 [MultiStageCoprocessor-other-example1-0] WARN  c.a.otter.canal.parse.inbound.mysql.tsdb.MemoryTableMeta - parse faield : ALTER USER 'canal'@'%' IDENTIFIED WITH 'mysql_native_password' AS '*6BB4837EB74329105EE4568DDA7DC67ED2CA2AD9'
com.alibaba.fastsql.sql.parser.ParserException: syntax error, expect PASSWORD, actual IDENTIFIER, pos 33, line 1, column 35, token IDENTIFIER IDENTIFIED
        at com.alibaba.fastsql.sql.parser.SQLParser.acceptIdentifier(SQLParser.java:71) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.fastsql.sql.dialect.mysql.parser.MySqlStatementParser.parseAlterUser(MySqlStatementParser.java:6805) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.fastsql.sql.dialect.mysql.parser.MySqlStatementParser.parseAlter(MySqlStatementParser.java:4660) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.fastsql.sql.parser.SQLStatementParser.parseStatementList(SQLStatementParser.java:283) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.fastsql.sql.SQLUtils.parseStatements(SQLUtils.java:536) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.fastsql.sql.repository.SchemaRepository.console(SchemaRepository.java:439) ~[fastsql-2.0.0_preview_855.jar:2.0.0_preview_855]
        at com.alibaba.otter.canal.parse.inbound.mysql.tsdb.MemoryTableMeta.apply(MemoryTableMeta.java:81) ~[canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.tsdb.DatabaseTableMeta.apply(DatabaseTableMeta.java:154) [canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.dbsync.TableMetaCache.apply(TableMetaCache.java:238) [canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.dbsync.LogEventConvert.parseQueryEvent(LogEventConvert.java:269) [canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.dbsync.LogEventConvert.parse(LogEventConvert.java:114) [canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.MysqlMultiStageCoprocessor$SimpleParserStage.onEvent(MysqlMultiStageCoprocessor.java:292) [canal.parse-1.1.3.jar:na]
        at com.alibaba.otter.canal.parse.inbound.mysql.MysqlMultiStageCoprocessor$SimpleParserStage.onEvent(MysqlMultiStageCoprocessor.java:246) [canal.parse-1.1.3.jar:na]
        at com.lmax.disruptor.BatchEventProcessor.processEvents(BatchEventProcessor.java:168) [disruptor-3.4.2.jar:na]
        at com.lmax.disruptor.BatchEventProcessor.run(BatchEventProcessor.java:125) [disruptor-3.4.2.jar:na]
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511) [na:1.8.0_201]
        at java.util.concurrent.FutureTask.run(FutureTask.java:266) [na:1.8.0_201]
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149) [na:1.8.0_201]
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624) [na:1.8.0_201]
        at java.lang.Thread.run(Thread.java:748) [na:1.8.0_201]

感觉这像是个权限问题，我给mysql中的canal用户赋了全部权限，就没问题了。
GRANT ALL PRIVILEGES ON *.* TO 'canal'@'%' ;
FLUSH PRIVILEGES;

版本v1.0.25
开启 tsdb之后， 出现这种错误。删除之后就好了




```
