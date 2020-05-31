## mongoDB

#### [How To Deploy And Manage MongoDB With Docker](https://phoenixnap.com/kb/docker-mongodb)

```
mount  host  /data/db folder to container  /mongoData

docker run -it -v /data/db:/mongoData -p 27017:27017 --restart=always --name mongodb -d mongo
                                            ^    ^
                                    host port    container port and keep 27017
                                    can set any
                                    port

You can run processes inside a container and outside on the same port. You can even run multiple containers using the same port internally. What you can't do is map the one port from the host to a container. Or in your, map a port that is already in use to a container.
services:
    webapp:
        image: myimage
        ports:
            - '3000:3000'

    mongo:
        image: 'mongo:latest'
        ports:
            - '27018:27017'      <------

    mongo2:
        image: mongo:latest
        ports:
            - '27019:27017'     <--------
```

#### [MongoDB 进阶模式设计](https://mongoing.com/mongodb-advanced-pattern-design)

#### [MongoDB提升性能的18原则（开发设计阶段）](https://blog.fundebug.com/2018/09/19/18-principle-to-improve-mongodb-performance/)

#### [Data Modeling Introduction](https://docs.mongodb.com/manual/core/data-modeling-introduction/)
#### [Data Model Examples and Patterns](https://docs.mongodb.com/manual/applications/data-models/)

#### [mongodb multiple groups in one result](https://stackoverflow.com/questions/23745097/mongodb-multiple-groups-in-one-result)

#### [mongodb 备份、还原、导出、导入](https://www.jianshu.com/p/667fd4fd6ff7)

#### [BSON及mongoDB数据类型的详解介绍](http://www.haiyang.me/read.php?key=697)
```
二、BSON特性

1、什么是BSON

    BSON（）是一种类json的一种二进制形式的存储格式，简称Binary JSON
    它和JSON一样，支持内嵌的文档对象和数组对象，但是BSON有JSON没有的一些数据类型，如Date和BinData类型。
    https://docs.mongodb.com/manual/reference/bson-types/
2、BSON的特定

    轻量性、可遍历性、高效性
```