
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

## Intellij Idea  license server

><https://gist.github.com/oct111992/383283462a2fa11defffbf401ecbdf7f>

## JAVA NIO 一步步构建I/O多路复用的请求模型

><https://github.com/jasonGeng88/blog/blob/master/201708/java-nio.md>

## intellij IDEA license code 

><https://gist.github.com/shanezhiu/815590f573b738cc80e94d55143f6db2>

```python
BTBV1R0CZR-eyJsaWNlbnNlSWQiOiJCVEJWMVIwQ1pSIiwibGljZW5zZWVOYW1lIjoiTXVzaGZpcXVyIFJhaG1hbiIsImFzc2lnbmVlTmFtZSI6IiIsImFzc2lnbmVlRW1haWwiOiIiLCJsaWNlbnNlUmVzdHJpY3Rpb24iOiJGb3IgZWR1Y2F0aW9uYWwgdXNlIG9ubHkiLCJjaGVja0NvbmN1cnJlbnRVc2UiOmZhbHNlLCJwcm9kdWN0cyI6W3siY29kZSI6IklJIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In0seyJjb2RlIjoiQUMiLCJwYWlkVXBUbyI6IjIwMTktMTEtMjgifSx7ImNvZGUiOiJEUE4iLCJwYWlkVXBUbyI6IjIwMTktMTEtMjgifSx7ImNvZGUiOiJQUyIsInBhaWRVcFRvIjoiMjAxOS0xMS0yOCJ9LHsiY29kZSI6IkdPIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In0seyJjb2RlIjoiRE0iLCJwYWlkVXBUbyI6IjIwMTktMTEtMjgifSx7ImNvZGUiOiJDTCIsInBhaWRVcFRvIjoiMjAxOS0xMS0yOCJ9LHsiY29kZSI6IlJTMCIsInBhaWRVcFRvIjoiMjAxOS0xMS0yOCJ9LHsiY29kZSI6IlJDIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In0seyJjb2RlIjoiUkQiLCJwYWlkVXBUbyI6IjIwMTktMTEtMjgifSx7ImNvZGUiOiJQQyIsInBhaWRVcFRvIjoiMjAxOS0xMS0yOCJ9LHsiY29kZSI6IlJNIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In0seyJjb2RlIjoiV1MiLCJwYWlkVXBUbyI6IjIwMTktMTEtMjgifSx7ImNvZGUiOiJEQiIsInBhaWRVcFRvIjoiMjAxOS0xMS0yOCJ9LHsiY29kZSI6IkRDIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In0seyJjb2RlIjoiUlNVIiwicGFpZFVwVG8iOiIyMDE5LTExLTI4In1dLCJoYXNoIjoiMTEwODc1NDYvMCIsImdyYWNlUGVyaW9kRGF5cyI6MCwiYXV0b1Byb2xvbmdhdGVkIjpmYWxzZSwiaXNBdXRvUHJvbG9uZ2F0ZWQiOmZhbHNlfQ==-wQ6zKQMYh4XcZ+Rq3FkZCo9kJe9iJYoD1+cxAhVr1oiKOA0ANleB1AiBwlpeIuq6IH9v+Xt3mfONBboolQtbCsSjSuOwphPVP77sK4dzR4Bp5h0IMTlYLTSfYx484VhhuYr74VQT/90iXfKb8E/mFqJZKQQIXOXjfPPeqPsrOToxuXVIbW/i6Sp6Y6bSBYKJp1xtxTxWb/tBn/5zKK5seWS6cb/pttMFXQIFKjma6HXGxNgAlpC5hz20rH3+z4/ltns3ve4rlFn0QtHkBBRqm1G6HKTQkIg/h1cw8aVq0GIGYG6Hol5SNK0wzMB5CTjTOZxCqPb0d5LI7/cXh/i4tw==-MIIElTCCAn2gAwIBAgIBCTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE4MTEwMTEyMjk0NloXDTIwMTEwMjEyMjk0NlowaDELMAkGA1UEBhMCQ1oxDjAMBgNVBAgMBU51c2xlMQ8wDQYDVQQHDAZQcmFndWUxGTAXBgNVBAoMEEpldEJyYWlucyBzLnIuby4xHTAbBgNVBAMMFHByb2QzeS1mcm9tLTIwMTgxMTAxMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQAF8uc+YJOHHwOFcPzmbjcxNDuGoOUIP+2h1R75Lecswb7ru2LWWSUMtXVKQzChLNPn/72W0k+oI056tgiwuG7M49LXp4zQVlQnFmWU1wwGvVhq5R63Rpjx1zjGUhcXgayu7+9zMUW596Lbomsg8qVve6euqsrFicYkIIuUu4zYPndJwfe0YkS5nY72SHnNdbPhEnN8wcB2Kz+OIG0lih3yz5EqFhld03bGp222ZQCIghCTVL6QBNadGsiN/lWLl4JdR3lJkZzlpFdiHijoVRdWeSWqM4y0t23c92HXKrgppoSV18XMxrWVdoSM3nuMHwxGhFyde05OdDtLpCv+jlWf5REAHHA201pAU6bJSZINyHDUTB+Beo28rRXSwSh3OUIvYwKNVeoBY+KwOJ7WnuTCUq1meE6GkKc4D/cXmgpOyW/1SmBz3XjVIi/zprZ0zf3qH5mkphtg6ksjKgKjmx1cXfZAAX6wcDBNaCL+Ortep1Dh8xDUbqbBVNBL4jbiL3i3xsfNiyJgaZ5sX7i8tmStEpLbPwvHcByuf59qJhV/bZOl8KqJBETCDJcY6O2aqhTUy+9x93ThKs1GKrRPePrWPluud7ttlgtRveit/pcBrnQcXOl1rHq7ByB8CFAxNotRUYL9IF5n3wJOgkPojMy6jetQA5Ogc8Sm7RG6vg1yow==
```
## oracle ask login to download jdk, fuck
> ## How to Install JAVA 8 on Ubuntu 18.04/16.04, Linux Mint 19/18
> <https://tecadmin.net/install-oracle-java-8-ubuntu-via-ppa/>

> ## How To Install Oracle Java 8 in Ubuntu 16.04
> <https://www.liquidweb.com/kb/how-to-install-oracle-java-8-in-ubuntu-16-04/>

> ## install Oracle jdk8u201 to centos 7
> <https://tecadmin.net/install-java-8-on-centos-rhel-and-fedora/>   
  [alternatives(update-alternatives) 的配置目录位置](https://my.oschina.net/weiyi/blog/2248648)

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
