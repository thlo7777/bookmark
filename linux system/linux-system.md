## ssh自动登录的实现方法
><https://www.jianshu.com/p/ad67893d36ea>

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

## centos7  firewall commnd
```
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