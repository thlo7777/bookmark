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

>//Install Docker
<https://kubernetes.io/docs/setup/cri/>
May be: 
cat \<\< EOF > /etc/docker/daemon.json
{
  "exec-opts": ["native.cgroupdriver=cgroupfs"]
}
EOF

>\#apt-get update && apt-get install -y apt-transport-https curl
\#curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
\#cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
\#apt-get update
\#apt-get install -y kubelet kubeadm kubectl
\#apt-mark hold kubelet kubeadm kubectl

>//update k8s configuration
\#vim /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
//Add the below after the last line
Environment="KUBELET_CGROUP_ARGS=--cgroup-driver=cgroupfs"