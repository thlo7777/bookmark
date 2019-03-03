# Install k8s step

>$ sudo su
\# apt-get udpate

**//turn off swap**
>\# swapoff -a

**//permenate turn off swap**
>\#vim /etc/fstab

**//update the hostname, input what you want, k8s-master or k8s-node**
>\#vim /etc/hostname  
>\#ifconfig

**//modify hosts: \<IP-address> hostnmae**
>\#vim /etc/hosts  
>\#vim /etc/network/interfaces  
auto enp0s8   
iface enp0s8 inet static    
address \<IP-address>   

>\#sudo apt-get install openssh-server

**//Install Docker**  
><https://kubernetes.io/docs/setup/cri/>   
May be:  
cat \<\< EOF > /etc/docker/daemon.json  
{   
  "exec-opts": ["native.cgroupdriver=cgroupfs"]   
}   
EOF

>\#apt-get update && apt-get install -y apt-transport-https curl    
\#curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -   
\#cat \<\<EOF >/etc/apt/sources.list.d/kubernetes.list    
deb https://apt.kubernetes.io/ kubernetes-xenial main   
EOF   
\#apt-get update    
\#apt-get install -y kubelet kubeadm kubectl  
\#apt-mark hold kubelet kubeadm kubectl   

**//update k8s configuration**
>\#vim /etc/systemd/system/kubelet.service.d/10-kubeadm.conf    
//Add the below after the last line   
Environment="KUBELET_CGROUP_ARGS=--cgroup-driver=cgroupfs"

**//Claico or flannel 10.244.0.0/16**
>\#kubeadm init --kubernetes-version v1.13.1 --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address=\<IP address>

**//如果 token忘记，则可以去 Master上执行如下命令来获取：**
>\#kubeadm token list


**//如果init出现了错误，需要重新init的时候，可以 #kubeadm reset 重新初始化集群。**
>\# kubeadm reset

>//设置用户环境变量和目录
\$ mkdir -p \$HOME/.kube
\$ sudo cp -i /etc/kubernetes/admin.conf \$HOME/.kube/config
\$ sudo chown $(id -u):$(id -g) \$HOME/.kube/config

>//如果 token忘记，则可以去 Master上执行如下命令来获取：
\# kubeadm token list

>//可以看到coredns的状态是pending,这事因为我们还没有安装网络插件
\$ sudo kubectl get pods --all-namespaces

>//安装calico网络组件
\$ kubectl apply -f <https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/rbac-kdd.yaml>
\$ kubectl apply -f https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml

>**//coredns crashloopbackoff in kubernetes**
\$ kubectl get pods --all-namespaces
kube-system coredns-86c58d9dfd      CrashLoopBckOff
<https://stackoverflow.com/questions/54466359/coredns-crashloopbackoff-in-kubernetes>
>//I have resolved this issue. In my case I had below contents of /etc/resolv.conf
nameserver     127.0.1.1
//I first used the below command to get the correct IP as the device was in client's network.
\$ nmcli device show \<interfacename> | grep IP4.DNS
//After this I updated the file /etc/resolvconf/resolv.conf.d/head with below contents
nameserver    192.168.66.21
nameserver    114.114.114.114
nameserver    8.8.8.8
//and then run the below command to regenerate the resolv.conf
\$ sudo vim /run/resolvconf/interface/NetworkManager
//remove nameserver 127.0.1.1
\$ sudo resolvconf -u
//After this I had below contents in /etc/resolv.conf:
nameserver    192.168.66.21
nameserver    114.114.114.114
nameserver    8.8.8.8

>//then delte coreDns 
\$ kubectl -n kube-system delete pod -l k8s-app=kube-dns