# spring cloud集群搭建


## 集群搭建
### 1. Eureka server

### 2. 网关

## 各种问题
### 1. IntelliJ IDEA maven库下载依赖包速度慢的问题

> 右键项目选中maven选项，然后选择“open settings.xml”或者 “create settings.xml”，然后把如下代码粘贴进去就可以了。重启IDE，感受速度飞起来的感觉吧！！！
```
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <mirrors>
        <!-- mirror
         | Specifies a repository mirror site to use instead of a given repository. The repository that
         | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
         | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
         |
        <mirror>
          <id>mirrorId</id>
          <mirrorOf>repositoryId</mirrorOf>
          <name>Human Readable Name for this Mirror.</name>
          <url>http://my.repository.com/repo/path</url>
        </mirror>
         -->

        <mirror>
            <id>alimaven</id>
            <name>aliyun maven</name>
            <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
            <mirrorOf>central</mirrorOf>
        </mirror>

        <mirror>
            <id>uk</id>
            <mirrorOf>central</mirrorOf>
            <name>Human Readable Name for this Mirror.</name>
            <url>http://uk.maven.org/maven2/</url>
        </mirror>

        <mirror>
            <id>CN</id>
            <name>OSChina Central</name>
            <url>http://maven.oschina.net/content/groups/public/</url>
            <mirrorOf>central</mirrorOf>
        </mirror>

        <mirror>
            <id>nexus</id>
            <name>internal nexus repository</name>
            <!-- <url>http://192.168.1.100:8081/nexus/content/groups/public/</url>-->
            <url>http://repo.maven.apache.org/maven2</url>
            <mirrorOf>central</mirrorOf>
        </mirror>

    </mirrors>
</settings>

--------------------- 
作者：但觉 
来源：CSDN 
原文：https://blog.csdn.net/qq1501340219/article/details/54638158 
版权声明：本文为博主原创文章，转载请附上博文链接！
```
### 2. logback、log4j、log4j2三种日志框架性能检测——为什么用log4j2
><https://blog.csdn.net/qq_32250495/article/details/82382052>

关于log4j2的新特性

+ 丢数据这种情况少，可以用来做审计功能。而且自身内部报的exception会被发现，但是logback和log4j不会。
+ log4j2使用了disruptor技术，在多线程环境下，性能高于logback等10倍以上。
+ (garbage free）之前的版本会产生非常多的临时对象，会造成GC频繁，log4j2则在这方面上做了优化，减少产生临时对象。尽可能少的GC
+ 利用插件系统，使得扩展新的appender,filter,layout等变得容易，log4j不可以扩展 插件？？？？
+ 因为插件系统的简单性，所以在配置的时候，可以不用具体指定所要处理的类型。class
+ 可以自定义level
+ Java 8 lambda support for lazy logging
+ Support for Message objects
+ 对filter的功能支持的更强大
+ 系统日志(Syslog)协议supports both TCP and UDP
+ 利用jdk1.5并发的特性，减少了死锁的发生。
+ Socket LogEvent SerializedLayout
+ 支持kafka queue

> ### 3. @RequestParam @RequestBody @PathVariable 等参数绑定注解详解
> ```
>    A、处理requet uri 部分（这里指uri template中variable，不含queryString部分）的注解：   @PathVariable;
>
>    B、处理request header部分的注解：   @RequestHeader, @CookieValue;
>
>    C、处理request body部分的注解：@RequestParam,  @RequestBody;
>
>    D、处理attribute类型是注解： @SessionAttributes, @ModelAttribute;
> ```     

> ### 4. classpath:与classpath*:有何区别
> 【classpath:】此配置表示告诉web容器去classpath（WEB-INF/classes和WEB-INF/lib）中去加载指定名称的配置文件，若是有同名文件，**则只会加载一个**。     
> 【classpath*:】此配置表示告诉web容器去classpath（WEB-INF/classes和WEB-INF/lib）中去加载指定名称的配置文件，若是有同名文件**则会全部加载**。      
> [ Spring加载配置文件classpath、classpath*、file解析](https://blog.csdn.net/shangmingtao/article/details/78311189)
> ````
>   /**
>    * Get current classpath
>    */
>   String path = Thread.currentThread().getContextClassLoader().getResource("").getPath();
>   System.out.println(path);
> ````