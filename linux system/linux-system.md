### [基于深度学习的目标检测技术演进：R-CNN、Fast R-CNN、Faster R-CNN](https://www.linuxidc.com/Linux/2017-06/145142.htm)

### [MacOS使用shadowsocks-libev+Simple-OBFS教程](https://medium.com/@yanlong/macos%E4%BD%BF%E7%94%A8shadowsocks-libev-simple-obfs%E6%95%99%E7%A8%8B-c10eba9c0758)
```
平时我们不会使用全局代理的，下来我们配置PAC自动代理。
```

### [在 macOS 中安装 shadowsocks-libev 和 simple-obfs](https://boris1993.github.io/tools/shadowsocks/install-shadowsocks-on-macosx.html)

### [Ubuntu 16.04下Shadowsocks服务器端安装及优化](https://www.polarxiong.com/archives/Ubuntu-16-04%E4%B8%8BShadowsocks%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E5%AE%89%E8%A3%85%E5%8F%8A%E4%BC%98%E5%8C%96.html)
```
本教程旨在提供简明的Ubuntu 16.04下安装服务器端Shadowsocks。不同于Ubuntu 16.04之前的教程，本文抛弃initd，转而使用Ubuntu 16.04支持的Systemd管理Shadowsocks的启动与停止，显得更为便捷。优化部分包括BBR、TCP Fast Open以及吞吐量优化。
```

### [Install Shadowsocks-libev + simple-obfs on Ubuntu](https://gist.github.com/nuhuo08/01cb865f77967a2ce14841d6d7fc1f02)
```
Install shadowsocks-libev via Ubuntu PPA
Install simple-obfs
```
### [Ubuntu Server 配置 Shadowsocks-libev 服务端（包括 simple-obfs）](https://medium.com/circumvention-technology/install-and-configure-shadowsocks-libev-and-simple-obfs-on-ubuntu-357e908a5546)
```
libev 版是因为此版本还在维护，特别注意不要使用 python 版尤其是从 python 源上下载的版本
```

## ssh自动登录的实现方法
><https://www.jianshu.com/p/ad67893d36ea>

### [Git管理多个SSH密钥，Git多帐号配置](https://blog.csdn.net/yanzhenjie1003/article/details/69487932)
>```text
>Git提交时有Https和SSH两种验证方式，Https的方式需要帐号和密码比较好理解，不过它需要在每次提交时输入帐号和密码，有点麻烦；
>而SSH的功能可以粗暴的理解为记住帐号密码，不过对这个过程有人会有点疑惑。首先，我们用SSH命令生成一个公钥-私钥对，我们会把公钥
>添加到Git的服务器，把私钥放在本地。提交文件的时候Git服务器会用公钥和客户端提交私钥做验证（具体细节不究），如果验证通过则提交成功，
>那么我们在把公钥添加到服务器的时候肯定是需要登录Git服务器的，这个过程其实可以理解为帐号和密码托管给SSH了，所以也是相当于输入了帐号密码，
>但是由SSH帮你记住了。这么理解是可以，但是SSH的意义不仅仅是这样，关于SSH的更详细内容看客可以自行再了解。
>```

## Tmux - Linux从业者必备利器
><http://cenalulu.github.io/linux/tmux/>

## Tmux 快捷键 & 速查表
><https://gist.github.com/ryerh/14b7c24dfd623ef8edc7>
## Install Ubuntu-16.04 LTS on Virtual Box (Desktop version)
><https://medium.com/@tushar0618/install-ubuntu-16-04-lts-on-virtual-box-desktop-version-30dc6f1958d0>

## Ubuntu 16.04 安装ss客户端
><https://blog.csdn.net/thor_w/article/details/79504804>

## VirtualBox虚拟机互通并共享主机IP
><https://www.jianshu.com/p/6a2cec8de3f1>

## VirtualBox中多个虚拟机之间互通及与宿主机互通配置
><https://zhuanlan.zhihu.com/p/40405167>

## ubuntu completely remove packages
>**list all installed packages**    
#sudo apt list --installed     
**remove packages**     
#apt-get remove --purge package     
#apt-get clean

## Error response from daemon: Get https://index.docker.io/v1/search?q=nginx&n=25: dial tcp: lookup index.docker.io on 127.0.1.1:53: read udp 127.0.0.1:47637->127.0.1.1:53: i/o timeout
>re-install (uninstall -> install) the same version docker.

## Ubuntu更新软件源出现GPG error
><https://blog.csdn.net/Timekeeperl/article/details/79173793>

## VirtualBox Guest Additions on Fedora 29/28, CentOS/RHEL 7.5/6.10/5.11
><https://www.if-not-true-then-false.com/2010/install-virtualbox-guest-additions-on-fedora-centos-red-hat-rhel/>

## How To Install VirtualBox Guest Additions on Fedora 29-25, CentOS 7/6
><https://tecadmin.net/install-virtualbox-guest-additions-fedora/>

## Install Docker in CentOS 7
><https://docs.docker.com/install/linux/docker-ce/centos/#prerequisites>

## How To Reset Root Password In CentOS 7
><http://www.linuxandubuntu.com/home/how-to-reset-root-password-in-centos-7>
#### [How To Reset Root Password On CentOS 7](https://www.unixmen.com/reset-root-password-centos-7/)

## centos7  firewall commnd
```
//Enable Firewalld
//To enable firewalld, run the following command as root:
# systemctl enable firewalld

//Start Firewalld
//To start firewalld, run the following command as root:
# systemctl start firewalld

//add port
$ sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
$ sudo firewall-cmd --permanent --zone=public --remove-port=10911/tcp

//To run the firewall must be reloaded using the following command
$ sudo firewall-cmd --reload

//list status
$  sudo firewall-cmd --list-all
//list all active zones
$  firewall-cmd --get-active-zones
//check fireall status 
$ systemctl status firewalld
$ firewall-cmd --set-default-zone=<zone>
$ firewall-cmd --permanent --zone=<zone> --add-service=http
$ firewall-cmd --permanent --zone=<zone> --add-port=80/tcp
$ firewall-cmd --list-ports
$ firewall-cmd --list-services
```

## CentOs 7 java force use IPV4

```bash
//add  environment variable  in bashrc or bash_profile
export _JAVA_OPTIONS="-Djava.net.preferIPv4Stack=true -Djava.net.preferIPv4Addresses=true"
```
>[参考java设置](http://mindprod.com/jgloss/javaexe.html#JAVAOPTIONS)

## Tmux install and remove
>[Update your tmux to latest version](http://witkowskibartosz.com/blog/update-your-tmux-to-latest-version.html#.XKwWRHWFPCI)
````
When first start tmux Use tmux kill-server, after that start a new tmux session.
````
>[tmux config github](https://github.com/gpakosz/.tmux)         
><https://www.ifmicro.com/%E8%BD%AF%E4%BB%B6/2015/05/05/tmux/>

## ssh config file
>[告诉你如何管理gitlab/github的ssh-key](https://juejin.im/post/5c063c4ee51d451ded182458)    
><https://www.hi-linux.com/posts/14346.html>    
><https://www.jianshu.com/p/6162b94110fc>

## 3 Ways to List All Installed Packages in RHEL, CentOS and Fedora
><https://www.tecmint.com/list-installed-packages-in-rhel-centos-fedora/>

## 每天一个linux命令（10）：cat 命令
><https://www.cnblogs.com/peida/archive/2012/10/30/2746968.html>

## Postman请求Https接口
><https://blog.csdn.net/ONS_cukuyo/article/details/79172242>

## systemctl 列出所有可用单元
```text
# systemctl list-unit-files
# systemctl status halt-local.service
在开机时启用一个服务：systemctl enable app-run.service  
在开机时禁用一个服务：systemctl disable app-run.service
启动一个服务：systemctl start app-run.service  
关闭一个服务：systemctl stop app-run.service  
重启一个服务：systemctl restart app-run.service  
显示一个服务的状态：systemctl status app-run.service    
查看服务是否开机启动：systemctl is-enabled app-run.service  
查看已启动的服务列表：systemctl list-unit-files|grep enabled  

```

#### [Centos 7 设置使用阿里云镜像做 yum 源](https://www.hotbak.net/key/%E9%98%BF%E9%87%8C%E4%BA%91yum%E9%95%9C%E5%83%8F%E6%BA%90.html)

#### [CentOS 7- 配置阿里镜像源](https://yq.aliyun.com/articles/704987)


### [ubuntu16.04 apt-get更换阿里源](https://blog.csdn.net/ypbsyy/article/details/81143017)
```text
1.备份系统自带源

　　mv /etc/apt/sources.list /etc/apt/sources.list.bak

2.修改/etc/apt/sources.list文件

　　vim /etc/apt/sources.list  

　　加入如下内容:
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse #Added by software-properties

deb http://archive.canonical.com/ubuntu xenial partner

deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse

```
#### [Centos内核优化](https://blog.csdn.net/jet19810906/article/details/80676786)

#### [The Shell Guru](https://www.theshell.guru/category/centos/)

#### [CentOS Liunx 7 更换为阿里云的源]
```
1、备份
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

2、下载新的CentOS-Base.repo 到/etc/yum.repos.d/
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

3、生成缓存
yum makecache
yum -y update

```

#### [How to yum update curl 7.29 to 7.61 - CentOS 7.X](https://qiita.com/tkprof/items/5460b8d603cbbc542c8c)

#### [Centos 7 忘记密码重置用户密码](https://www.jianshu.com/p/581c0444d627)

#### [VirtualBox Configure a Static IP on CentOS 7](https://qiita.com/Tutorial/items/5ab1ec4ba55396b089f8)
```
virtual box 6.0 config host only with virtual machine
1. firstlly to install virtualbox guest addtionals
2. then create host only network adaptor in VB menu 管理->主机网络管理器
3. Configure a Static IP on CentOS
    Login with 'root' user.

    Edit ifcfg-enp0s3 file as per the following code. (In vi editor, use 'i' for insert, 'esc' key to enter command mode and 'wq' for save and quit)

    vi /etc/sysconfig/network-scripts/ifcfg-enp0s3

    ONBOOT=yes
    USERCTL=no
    Edit ifcfg-enp0s8 file as per the following code. (Note. IPADDR value should be in between Lower Address Bound and Upper Address Bound values)
    vi /etc/sysconfig/network-scripts/ifcfg-enp0s8

    BOOTPROTO=none
    ONBOOT=yes
    IPADDR=192.168.56.141
    PREFIX=24
    Restart network
    systemctl restart network
    Test with the ping command, try it in a Windows Command Prompt window (CMD).
```

#### [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/18.04/)

#### [Ubuntu 镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)


#### [How to Install Xrdp Server (Remote Desktop) on Ubuntu 18.04](https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-18-04/)

#### [TengDa U9 移动WiFi](https://github.com/brektrou/rtl8821CU)
```
ubuntu 更新kernel 以后 需要 copy  realtek.ro to kernal libarary
If you successfully install the driver, the driver is installed on /lib/modules/<linux version>/kernel/drivers/net/wireless/realtek/rtl8821cu. Check the driver with the ls command:

ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/realtek/rtl8821cu
Make sure 8821cu.ko file present on that directory
```