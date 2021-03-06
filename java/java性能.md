# java 服务器 性能比较

- #### [Testing the Performance of NGINX and NGINX Plus Web Servers](https://www.nginx.com/blog/testing-the-performance-of-nginx-and-nginx-plus-web-servers/)
```
   We all know that performance is critical to a website’s success. No one wants to use a slow website.
 Since its initial open source release in 2004, NGINX has been synonymous with high‑performance websites. 
   66% of the world’s top 100,000 websites, and over 358 million sites worldwide are now powered by NGINX. 
 But how well does NGINX actually perform? What hardware configurations will yield the best performance 
 at a reasonable price?
   To answer these questions, we went into the lab and performance‑tested NGINX in two configurations: 
 as a reverse proxy and as a web server. 
   We published the reverse proxy performance numbers in our NGINX Plus Sizing Guide for Bare Metal Servers
   and detailed how the testing was done in our blog NGINX Plus Sizing 
```
- #### [使用四种框架分别实现百万websocket常连接的服务器](http://www.importnew.com/23293.html)
```text
本文是我在实践过程中的记录，我的目标是使用spran-websocket，netty, undertow和node.js四种框架分别实现C1000K的服务器，
看看这几个框架实现的难以程度，性能如何。开发语言为Scala和Javascript。
```

- #### [Centos7高并发优化](https://my.oschina.net/shyloveliyi/blog/2979058)

- #### [SpringBoot服务器压测对比（jetty、tomcat、undertow）](https://my.oschina.net/shyloveliyi/blog/2980440)
```text
1、本次对比基础环境信息如下：

    springboot版本1.5.10

    centos虚机4c6G，版本7.4

    centos实机2u16c40G，版本7.4，虚机运行在实机上

    ab版本2.3

    jprofiler版本9.1.1
```

- #### [后续之《SpringBoot服务器压测对比（jetty、tomcat、undertow）》](https://my.oschina.net/shyloveliyi/blog/2980868)
```text
 HTTP异步的目的在帮助dispatcherservlet分担压力，提升吞吐量。但如果运行在NIO模式的服务容器上，就会产生负面影响，
 因为NIO本身就做了类似的事情，此时再加HTTP异步，则相当于又加了N多不必要的线程，导致性能主要消耗在线程的开销上，
 所以建议使用tomcat作为内嵌容器并且**没有开启tomcat的NIO模式时，可以配合HTTP异步来提升程序性能**。
 尤其是当业务繁重时，提升效果尤其明显。
```

- ####[The C10K problem](http://www.kegel.com/c10k.html)
```
It's time for web servers to handle ten thousand clients simultaneously, don't you think?
After all, the web is a big place now.
```

- ####[Document recommendation about using netty-tcnative for optimizing TLS performance #344](https://github.com/reactor/reactor-netty/issues/344)
```text
Speed: In local testing, we've seen performance improvements of 3x over the JDK. GCM, which is used 
by the only cipher suite required by the HTTP/2 RFC, is 10-500x faster.
```

- #### [Linux上Jvm性能调优方法](https://blog.csdn.net/lvdeqing/article/details/54381716)
```text
OS 诊断
先考察Linux操作系统上显示的性能指标，主要关注CPU、Memory、I/O三方面：
```
- #### [JVM调优之jstack找出最耗cpu的线程并定位代码](https://www.cnblogs.com/chengJAVA/p/5821218.html)
```text
jstack可以定位到线程堆栈，根据堆栈信息我们可以定位到具体代码，所以它在JVM性能调优中使用得非常多。下面我们来一个实例找出某个Java进程中最耗费CPU的Java线程并定位堆栈信息，
用到的命令有ps、top、printf、jstack、grep。
```
- #### [A Look at ForkJoinPool and Parallel Streams](https://dzone.com/articles/a-look-at-forkjoinpool)

- #### [Be Aware of ForkJoinPool#commonPool()](https://dzone.com/articles/be-aware-of-forkjoinpoolcommonpool)
- #### [Spring Cloud Feign 性能优化](https://www.jianshu.com/p/fe1c4412de7f)
- #### [API Gateway实现比较](https://github.com/chanjarster/api-gateways-comparison)
- #### [API网关性能比较](https://chanjarster.github.io/post/api-gateway-perf-comparison/)
- #### [性能测试 —— Spring Cloud Gateway、Zuul 基准测试](http://www.iocoder.cn/Performance-Testing/SpringCloudGateway-Zuul-benchmark/?vip)
- #### [Nginx tuning tips: TLS/SSL HTTPS – Improved TTFB/latency](https://haydenjames.io/nginx-tuning-tips-tls-ssl-https-ttfb-latency/)
- #### [Spring boot async controller with ResponseBodyEmitter](https://howtodoinjava.com/spring-boot2/spring-async-controller-responsebodyemitter/)

### [亿级流量系统架构之如何设计全链路99.99%高可用架构【石杉的架构笔记】](https://juejin.im/post/5bffab686fb9a04a102f0022)
```
百亿流量级别高并发写入场景下，如何承载这种高并发写入，
同时如何在高并发写入的背景下还能保证系统的超高性能计算。
```

### [如何设计一个高并发系统？](https://github.com/doocs/advanced-java/blob/master/docs/high-concurrency/high-concurrency-design.md)
```
假设你在某知名电商公司干过高并发系统，用户上亿，一天流量几十亿，高峰期并发量上万，甚至是十万。那么人家一定
会仔细盘问你的系统架构，你们系统啥架构？怎么部署的？部署了多少台机器？缓存咋用的？MQ 咋用的？数据库咋用的？
就是深挖你到底是如何扛住高并发的。
```

### [深入分析Netty的高性能](https://cloud.tencent.com/developer/article/1626515)