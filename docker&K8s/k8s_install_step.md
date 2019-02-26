# Install k8s step

>$ sudo su
\# apt-get udpate

>//turn off swap
\# swapoff -a
//permenate turn off swap
\#vim /etc/fstab

>//update the hostname, input what you want, k8s-master or k8s-node
\#vim /etc/hostname

>\#ifconfig
//modify hosts: \<IP-address> hostnmae
\#vim /etc/hosts

>\#vim /etc/network/interfaces
auto enp0s8
iface enp0s8 inet static
address \<IP-address>

>\#sudo apt-get install openssh-server
