
## 深入理解 Java 虚拟机

><http://wiki.jikexueyuan.com/project/java-vm/>

## 多线程死锁的产生以及如何避免死锁

><https://blog.csdn.net/ls5718/article/details/51896159>

## Java并发编程：volatile关键字解析

><https://www.cnblogs.com/dolphin0520/p/3920373.html>

## 设计模式

><http://www.runoob.com/design-pattern/observer-pattern.html>

## 图说设计模式

><https://design-patterns.readthedocs.io/zh_CN/latest/index.html>

## 一看你就懂，超详细java中的ClassLoader详解

><https://blog.csdn.net/briblue/article/details/54973413>

## Java线程池是如何诞生的？

><https://zhuanlan.zhihu.com/p/35188214>

## Java 流(Stream)、文件(File)和IO

><http://www.runoob.com/java/java-files-io.html>


## JAVA NIO 一步步构建I/O多路复用的请求模型

><https://github.com/jasonGeng88/blog/blob/master/201708/java-nio.md>


## oracle ask login to download jdk, fuck
>```text
>Download jdk8u from oracle, 
>$ sudo mkdir /usr/lib/jvm
>$ cd /usr/lib/jvm
>$ sudo tar zxvf jdk8u tgz
>
>vim /etc/environment
>    JAVA_HOME=/usr/lib/jvm/java-8-oracle
>    JRE_HOME=/usr/lib/jvm/java-8-oracle/jre
>
>~/.bashrc 
>    export PATH="$PATH:$JAVA_HOME/bin"
>
>```
> ## How to Install JAVA 8 on Ubuntu 18.04/16.04, Linux Mint 19/18
> <https://tecadmin.net/install-oracle-java-8-ubuntu-via-ppa/>
> ## How To Install Oracle Java 8 in Ubuntu 16.04
> <https://www.liquidweb.com/kb/how-to-install-oracle-java-8-in-ubuntu-16-04/>
> ## install Oracle jdk8u201 to centos 7
> <https://tecadmin.net/install-java-8-on-centos-rhel-and-fedora/>   
>  [alternatives(update-alternatives) 的配置目录位置](https://my.oschina.net/weiyi/blog/2248648)

## java 打包命令
>1. mkdir app folder
>2. mkdir app/classes
>3. coding java file with package, import etc
>4. javac YourFileName.java -d ./classes  生成目录根据package
>5. vim MANIFEST.MF
>6. jar -cmf MANIFEST.MF youname.jar -C classes/  .  生成jar包

## java 据算对象大小
>[java 一个字节占用多少内存](https://yueyemaitian.iteye.com/blog/2033046)
1. Use java Instrumentation package 类统计, create InstrumentationAgent.java
````
package com.dream.getObjectSize;

import java.lang.instrument.Instrumentation;
import java.lang.reflect.Array;
import java.lang.reflect.Field;
import java.lang.reflect.Modifier;
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.HashSet;
import java.util.Set;

/**
 * 对象占用字节大小工具类
 *
 * @author tianmai.fh
 * @date 2014-03-18 11:29
 */

public class InstrumentationAgent {

    private static volatile Instrumentation globalInstrumentation;

    public static void premain(final String agentArgs, final Instrumentation inst) {
        globalInstrumentation = inst;
    }

    /**
     * 直接计算当前对象占用空间大小，包括当前类及超类的基本类型实例字段大小、<br></br>
     * 引用类型实例字段引用大小、实例基本类型数组总占用空间、实例引用类型数组引用本身占用空间大小;<br></br>
     * 但是不包括超类继承下来的和当前类声明的实例引用字段的对象本身的大小、实例引用数组引用的对象本身的大小 <br></br>
     *
     * @param object
     * @return
     */
    public static long getObjectSize(final Object object) {
        if (globalInstrumentation == null) {
            throw new IllegalStateException("Agent not initialized.");
        }
        return globalInstrumentation.getObjectSize(object);
    }


    /**
     * 递归计算当前对象占用空间总大小，包括当前类和超类的实例字段大小以及实例字段引用对象大小
     *
     * @param objP
     * @return
     * @throws IllegalAccessException
     */
    public static long fullSizeOf(Object objP) throws IllegalAccessException {
        Set<Object> visited = new HashSet<Object>();
        Deque<Object> toBeQueue = new ArrayDeque<Object>();
        toBeQueue.add(objP);
        long size = 0L;
        while (toBeQueue.size() > 0) {
            Object obj = toBeQueue.poll();
            //sizeOf的时候已经计基本类型和引用的长度，包括数组
            size += skipObject(visited, obj) ? 0L : getObjectSize(obj);
            Class<?> tmpObjClass = obj.getClass();
            if (tmpObjClass.isArray()) {
                //[I , [F 基本类型名字长度是2
                if (tmpObjClass.getName().length() > 2) {
                    for (int i = 0, len = Array.getLength(obj); i < len; i++) {
                        Object tmp = Array.get(obj, i);
                        if (tmp != null) {
                            //非基本类型需要深度遍历其对象
                            toBeQueue.add(Array.get(obj, i));
                        }
                    }
                }
            } else {
                while (tmpObjClass != null) {
                    Field[] fields = tmpObjClass.getDeclaredFields();
                    for (Field field : fields) {
                        if (Modifier.isStatic(field.getModifiers())   //静态不计
                                || field.getType().isPrimitive()) {    //基本类型不重复计
                            continue;
                        }

                        field.setAccessible(true);
                        Object fieldValue = field.get(obj);
                        if (fieldValue == null) {
                            continue;
                        }
                        toBeQueue.add(fieldValue);
                    }
                    tmpObjClass = tmpObjClass.getSuperclass();
                }
            }
        }
        return size;
    }

    /**
     * String.intern的对象不计；计算过的不计，也避免死循环
     *
     * @param visited
     * @param obj
     * @return
     */
    static boolean skipObject(Set<Object> visited, Object obj) {
        if (obj instanceof String && obj == ((String) obj).intern()) {
            return true;
        }
        return visited.contains(obj);
    }

}
````
2. 使用打包命令生成 InstrumentationAgent.jar包      
MANIFEST.MF 如下：
```
Premain-class: com.dream.getObjectSize.InstrumentationAgent
Can-Redefine-Classes: false
```     
3. Intellij 导入 jar包
>3.1 在project工程中创建lib目录, copy InstrumentationAgent.jar到这里     
>3.2 Intellij->File->Project Structure->Libraries-> + 增加jar包      
>3.3 Maven添加dependency
```
    <dependency>
        <groupId>com.dream.getObjectSize</groupId>
        <artifactId>InstrumentationAgent</artifactId>
        <version>1.0</version>
        <scope>system</scope>
        <systemPath>${project.basedir}/lib/InstrumentationAgent.jar</systemPath>
    </dependency>
```
4. Intellij project 工程参数 应用Edit configurations -> VM options
```text
-javaagent:"/home/user/IdeaProjects/sso-demo/thymeleaf-demo/lib/InstrumentationAgent.jar"
```
5. Run project

## Java中文键树的一种实现（附带模糊查询功能）
><https://blog.csdn.net/yuhk231/article/details/51539840>

## java8的HashMap详解（存储结构，功能实现，扩容优化，线程安全，遍历方法）
><https://blog.csdn.net/login_sonata/article/details/76598675>


## 浅谈JDK动态代理
><https://zhuanlan.zhihu.com/p/62660956>

## mybatis <--> mysql 日期字段
```text
 MyBatis3做数据持久层，在字段中有Date和DateTime类型，在插入数据时只要将实体的属性设置成Timestamp就会
对应mysql的DateTime类型，Date会对应mysql的Date类型。
```

## keytool 制作证书
keytool -genkey -alias ssltest -keypass 1234 -keyalg RSA -keysize 1024 -validity 365 -storetype PKCS12 -keystore ssltest-keystore.p12 -storepass 123456

## 各种 Java 的序列化库的性能比较测试结果
><http://developer.51cto.com/art/201506/480273.htm>
## 实战Redis序列化性能测试(Kryo和字符串)
><https://blog.csdn.net/boling_cavalry/article/details/80719683>

#### [Be Aware of ForkJoinPool#commonPool()](https://dzone.com/articles/be-aware-of-forkjoinpoolcommonpool)
#### [Default ForkJoinPool executor taking long time](https://stackoverflow.com/questions/45460577/default-forkjoinpool-executor-taking-long-time)
#### [Performance Issues with newFixedThreadPool vs newSingleThreadExecutor](https://stackoverflow.com/questions/16125626/performance-issues-with-newfixedthreadpool-vs-newsinglethreadexecutor)
#### [java-cef](https://bitbucket.org/chromiumembedded/java-cef/src/master/)
```
Java Chromium Embedded Framework (JCEF). A simple framework for embedding Chromium-based browsers in other 
applications using the Java programming language.
```

#### [JCEF (Java Chromium Embedded Framework) build guide for windows](https://www.youtube.com/watch?v=Iran0zj0Za4)

#### [Java并发系列（1）AbstractQueuedSynchronizer源码分析之概要分析](https://www.cnblogs.com/liuyun1995/p/8400663.html)

#### [浅析Java中的final关键字](https://www.cnblogs.com/dolphin0520/p/3736238.html)
```
使用final方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。在早期的Java实现版本中，会将final方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升。在最近的Java版本中，不需要使用final方法进行这些优化了。

很多时候会容易把static和final关键字混淆，static作用于成员变量用来表示只保存一份副本，而final的作用是用来保证变量不可变。
```

#### [关于Java的权限修饰符(public,private,protected,默认friendly)](https://www.cnblogs.com/DreamDrive/p/4641676.html)

![java](data:image/png;base64,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)