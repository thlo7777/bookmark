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

## centos7  firewall commnd
```
//add port
$ sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
//To run the firewall must be reloaded using the following command
$ firewall-cmd --reload

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