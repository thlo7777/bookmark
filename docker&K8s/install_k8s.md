# install issue

## 1. ```curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ```

>**return gpg: no valid OpenPGP data found**
>You can manually download that file ```https://packages.cloud.google.com/apt/doc/apt-key.gpg``` and then do        
`cat apt-get.pgp | apt-key add -`       
<https://github.com/dart-lang/sdk/issues/34967>

## kubernetes安装（国内环境）
><https://zhuanlan.zhihu.com/p/46341911>

## too hard to install k8s in china
><https://github.com/kubernetes/kubernetes/issues/56038>

## 5分钟创建Amazon EC2实例 – AWS入门
><https://51daiwei.net/create-amazon-ec2>

## AWS系列-添加购买的https证书
><https://www.cnblogs.com/syaving/p/9029243.html>

## Kubernetes Ingress
><https://medium.com/@cashisclay/kubernetes-ingress-82aa960f658e>

## 烂泥：k8s安装与配置ingress(一)
><https://www.ilanni.com/?p=14501#%E4%B8%80%E3%80%81ingress%E4%BB%8B%E7%BB%8D>

## kunernets使用helm安装tiller踩坑
><https://www.jianshu.com/p/d0cdbb49569b>

## Kubernetes Commands
><https://gist.github.com/edsiper/fac9a816898e16fc0036f5508320e8b4#pods>

## kunernets使用helm安装tiller踩坑
><https://www.jianshu.com/p/d0cdbb49569b>

**helm reset -f not working**
>current workaround I'm using
```
$ kubectl get pods -n kube-system | grep tiller
tiller-deploy-674ff75566-r5658                          1/1       Running   0          2d
$ helm reset --force
Tiller (the Helm server-side component) has been uninstalled from your Kubernetes Cluster.
$ kubectl delete pods -n kube-system -l=name=tiller
pod "tiller-deploy-674ff75566-r5658" deleted
$ sleep 20
$ helm init --history-max=20 --debug --upgrade \ # collapsed multi-line command
```

**helm install not working**
```
//remove tiller
$  kubectl delete deployment tiller-deploy --namespace kube-system
$  create serviceaccount --namespace kube-system tiller
$ kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
$ helm init --service-account tiller
```
