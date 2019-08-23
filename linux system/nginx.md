### nignx 资料

#### [Nginx开发从入门到精通](http://tengine.taobao.org/book/)
```text
    nginx由于出色的性能，在世界范围内受到了越来越多人的关注，在淘宝内部它更是被广泛的使用，
众多的开发以及运维同学都迫切的想要了解nginx模块的开发以及它的内部原理，但是国内却没有一本
关于这方面的书，源于此我们决定自己来写一本。本书的作者为淘宝核心系统服务器平台组的成员，本书
写作的思路是从模块开发逐渐过渡到nginx原理剖析。书籍的内容会定期在这里更新，欢迎大家提出宝贵意见，
不管是本书的内容问题，还是字词错误，都欢迎大家提交issue(章节标题的左侧有评注按钮)，我们会及时的跟进。
```

#### [大型网站高并发处理Nginx+lvs](https://blog.csdn.net/qq_38982845/article/details/83593904)
```text
一.负载均衡
为啥会出现负载均衡
在海量并发的环境下，用户每一次请求服务器，都需要大量的创建线程，每一次的线程都必须分配资源（CPU、内存、带宽、磁盘 IO等），
当资源不足的时候就会使得服务器宕机而无法提供服务。那么如何保证网站在流量峰值时能够顺利运作呢? 首先来介绍几个概念

1.高并发
见名知意，高（大量的），并发就是可以使用多个线程或者多个进程，同时处理（就是并发）不同的操作。简而言之就是每秒内
有多少个请求同时访问。
```

#### [关于LVS+Nginx为什么会被同时使用的思考](https://blog.csdn.net/BuquTianya/article/details/52076153)
```
最初的理解
(也可以每个nginx都挂在上所有的应用服务器) 
nginx大家都在用，估计也很熟悉了，在做负载均衡时很好用，安装简单、配置简单、相关材料也特别多。

lvs是国内的章文嵩博士的大作，比nginx被广泛接受还要早7年，并且已经被红帽作为了系统内置软件，可谓很牛了。lvs相对于
nginx来说配置上就要相对复杂一些。

但是，有时候我们会看到大牛们分享的经验里面是lvs+nginx作为负载均衡了，一直想不明白这是个什么道理。

为什么会出现两者被同时使用呢？其实，这要从两者的各自优势来说了。
```
#### [部署NGINX Plus作为API网关（第一部分）——NGINX](https://cloud.tencent.com/developer/article/1149103)
```
作为领先的高性能、轻量级反向代理和负载均衡器解决方案，NGINX Plus具有处理API流量所需的高级HTTP处理能力。
这使得NGINX Plus成为构建API网关的理想平台。在本文中，我们将使用一些常见的API网关为例展示如何配置NGINX Plus
来以高效、可扩展、易维护的方式处理它们。最后我们会得到一套可作为生产环境部署基础的完整配置。

注：除特殊注明外，本文中所有的配置同时适用于NGINX和NGINX Plus。
```
#### [How to Build Nginx from source on CentOS 7](https://www.howtoforge.com/how-to-build-nginx-from-source-on-centos-7/)
```
In comparison with some other UNIX/Linux software, Nginx is pretty lightweight and doesn’t have many library dependencies. 
The default build configuration depends on only 3 libraries to be installed: OpenSSL/LibreSSL/BoringSSL, Zlib and PCRE.
```
***
> 编译问题 **[emerg] getpwnam("nginx") failed**  
> [nginx server cannot restart using service nginx start](https://stackoverflow.com/questions/38147412/nginx-server-cannot-restart-using-service-nginx-start)  
>   
>  If you’re compiling Nginx from source, you might be specifying the  
>  user and group flags at compile time.  
>  If this is the case, you need to ensure that the users actually exist  
>  when you attempt to start Nginx.  
>  How to fix getpwnam(“nginx”) failed  
>  It’s easy to fix this issue, simply create the specified user (in
>  this  
>  case, ‘nginx’) by issuing the following command:  
>  useradd nginx