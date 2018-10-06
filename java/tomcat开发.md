# 设计模式分析 - Tomcat 系统架构与设计模式，第 2 部分
https://www.ibm.com/developerworks/cn/java/j-lo-tomcat2/index.html
# 在IntelliJ IDEA 和 Eclipse运行tomcat 7源代码（Tomcat源代码阅读系列之一）
https://www.tuicool.com/articles/Rz6Fnyf
# Java 开发
https://www.ibm.com/developerworks/cn/java/
# Tomcat处理HTTP请求源码分析（上）
http://www.infoq.com/cn/articles/zh-tomcat-http-request-1
# Spring Boot Embedded Tomcat Performance
https://stackoverflow.com/questions/40319869/spring-boot-embedded-tomcat-performance
# Spring Boot切换为APR模式
https://www.cnblogs.com/xing901022/p/9145914.html

# Tomcat application folder structure
app name/
    WEB-INF/web.xml
    WEB-INF/classes/
    WEB-INF/lib/
    index.html
    *.jsp etc

The actual directory and file hierarchy used to contain the source code of an application can be pretty much anything you like. However, the following organization has proven to be quite generally applicable, and is expected by the example build.xml configuration file that is discussed below. All of these components exist under a top level project source directory for your application:
* docs/ - Documentation for your application, in whatever format your development team is using.

* src/ - Java source files that generate the servlets, beans, and other Java classes that are unique to your application. If your source code is organized in packages (highly recommended), the package hierarchy should be reflected as a directory structure underneath this directory.

* web/ - The static content of your web site (HTML pages, JSP pages, JavaScript files, CSS stylesheet files, and images) that will be accessible to application clients. This directory will be the document root of your web application, and any subdirectory structure found here will be reflected in the request URIs required to access those files.

* web/WEB-INF/ - The special configuration files required for your application, including the web application deployment descriptor (web.xml, defined in the Servlet Specification), tag library descriptors for custom tag libraries you have created, and other resource files you wish to include within your web application. Even though this directory appears to be a subdirectory of your document root, the Servlet Specification prohibits serving the contents of this directory (or any file it contains) directly to a client request. Therefore, this is a good place to store configuration information that is sensitive (such as database connection usernames and passwords), but is required for your application to operate successfully.
During the development process, two additional directories will be created on a temporary basis:
* build/ - When you execute a default build (ant), this directory will contain an exact image of the files in the web application archive for this application. Tomcat allows you to deploy an application in an unpacked directory like this, either by copying it to the $CATALINA_BASE/webapps directory, or by installing it via the "Manager" web application. The latter approach is very useful during development, and will be illustrated below. 

* dist/ - When you execute the ant dist target, this directory will be created. It will create an exact image of the binary distribution for your web application, including an license information, documentation, and README files that you have prepared.
403 Access Denied on Tomcat 9 Manager App without prompting for user/password
Find the CATALINA_HOME/webapps/manager/META-INF/context.xml file and add the comment markers around the Valve.
\<Context antiResourceLocking="false" privileged="true" > <br>
\<!—\<Valve className="org.apache.catalina.valves.RemoteAddrValve" allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /\><br>
\</Context\>

http://tomcat.apache.org/tomcat-8.0-doc/manager-howto.html#Configuring_Manager_Application_Access

# Tomcat install to mac sierra
https://wolfpaulus.com/mac/tomcat/
https://www.howtoforge.com/tutorial/how-to-install-apache-tomcat-8-5-on-ubuntu-16-04/
https://www.techrepublic.com/article/how-to-install-apache-tomcat-on-ubuntu-server-16-04/

# install tomcat 9 on ubuntu
https://tecadmin.net/install-tomcat-9-on-ubuntu/<br>
进入tomcat的bin目录 
cd $CATALINA_HOME/bin vi catalina.sh 找到 
OS specific support，然后在这行下面添加以下配置 
OS specific support. $var _must_ be set to either true or false. 

**Thlo added**
JAVA_HOME=/usr/lib/jvm/java-8-oracle<br>
JRE_HOME=/usr/lib/jvm/java-8-oracle/jre<br>
CATALINA_HOME=/opt/tomcat9<br>

#保存退出
# Linux服务器安装配置tomcat
http://www.jianshu.com/p/b71296e8b9a7

# TOMCAT原理详解及请求过程
http://www.cnblogs.com/hggen/p/6264475.html
https://www.packtpub.com/books/content/overview-tomcat-6-servlet-container-part-1
# Tomcat 系统架构与设计模式—工作原理
https://yq.aliyun.com/articles/74228
# Jetty和Tomcat的使用及性能测试
http://www.cnblogs.com/zhangxiaojun/archive/2013/02/07/2908619.html

# What is Tomcat default administrator password
http://www.mkyong.com/tomcat/tomcat-default-administrator-password/

# Installing Tomcat on macOS 10.13 High Sierra
https://wolfpaulus.com/mac/tomcat/
