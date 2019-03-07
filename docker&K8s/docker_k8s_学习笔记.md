# Docker和kubenetes学习笔记

> Thlo 2019/02/02

## 基本知识点

+ Cluster

+ Master

> Master 运行 Linux 操作系统，可以是物理机或者虚拟机。为了实现高可用，可以运行多个 Master。

+ **Node**

> Node 的职责是运行容器应用。Node 由 Master 管理，Node 负责监控并汇报容器的状态，并根据 Master 的要求管理容器的生命周期。Node 运行在 Linux 操作系统，可以是物理机或者是虚拟机。

+ **Pod**

>Pod 是 Kubernetes 的最小工作单元。每个 Pod 包含一个或多个容器。Pod 中的容器会作为一个整体被 Master 调度到一个 Node 上运行。
Kubernetes 引入 Pod 主要基于下面两个目的：

>1. 可管理性。
有些容器天生就是需要紧密联系，一起工作。Pod 提供了比容器更高层次的抽象，将它们封装到一个部署单元中。Kubernetes 以 Pod 为最小单位进行调度、扩展、共享资源、管理生命周期。
>2. 通信和资源共享。
Pod 中的所有容器使用同一个网络 namespace，即相同的 IP 地址和 Port 空间。它们可以直接用 localhost 通信。同样的，这些容器可以共享存储，当 Kubernetes 挂载 volume 到 Pod，本质上是将 volume 挂载到 Pod 中的每一个容器。

>Pods 有两种使用方式：
>1. 运行单一容器。
one-container-per-Pod 是 Kubernetes 最常见的模型，这种情况下，只是将单个容器简单封装成 Pod。即便是只有一个容器，Kubernetes 管理的也是 Pod 而不是直接管理容器。
>2. 运行多个容器。
但问题在于：哪些容器应该放到一个 Pod 中？ 
答案是：这些容器联系必须 非常紧密，而且需要 直接共享资源。

+ **kubernetes官方默认策略是worker节点运行Pod，master节点不运行Pod**

><https://pic4.zhimg.com/v2-c91d51eac851d4e8c845d7af5a98b6b3_r.jpg>

## kubernetes Objects

>A Kubernetes object is a “record of intent”–once you create the object, the Kubernetes system will constantly work to ensure that object exists.
**To work with Kubernetes objects–whether to create, modify, or delete them–you’ll need to use the Kubernetes API.**

## Kubernetes之Pause容器

>kubernetes中的pause容器便被设计成为每个业务容器提供以下功能：
>+ 在pod中担任Linux命名空间共享的基础；
>+ 启用pid命名空间，开启init进程。

## Secrets
>Kubernetes secret objects let you store and manage sensitive information, such as passwords, OAuth tokens, and ssh keys. Putting this information in a secret is safer and more flexible than putting it verbatim in a Pod Lifecycle definition or in a container image.
<https://kubernetes.io/docs/concepts/configuration/secret/#overview-of-secrets>

**Use Cases**

1. As a user, I want to store secret artifacts for my applications and consume them securely in containers, so that I can keep the configuration for my applications separate from the images that use them:        
  i. As a cluster operator, I want to allow a pod to access the Kubernetes master using a custom .kubeconfig file, so that I can securely reach the master      
ii. As a cluster operator, I want to allow a pod to access a Docker registry using credentials from a .dockercfg file, so that containers can push images       
iii. As a cluster operator, I want to allow a pod to access a git repository using SSH keys, so that I can push to and fetch from the repository        
2. As a user, I want to allow containers to consume supplemental information about services such as username and password which should be kept secret, so that I can share secrets about a service amongst the containers in my application securely        
3. As a user, I want to associate a pod with a ServiceAccount that consumes a secret and have the kubelet implement some reserved behaviors based on the types of secrets the service account consumes:     
i. Use credentials for a docker registry to pull the pod's docker image     
ii. Present Kubernetes auth token to the pod or transparently decorate traffic between the pod and master service       
4. As a user, I want to be able to indicate that a secret expires and for that secret's value to be rotated once it expires, so that the system can help me follow good practices

## PersistentVolumeClaims and PersistentVolumes
>A **PersistentVolume (PV)** is a piece of storage in the cluster that has been provisioned by an administrator. It is a resource in the cluster just like a node is a cluster resource.        
A **PersistentVolumeClaim (PVC)** is a request for storage by a user. It is similar to a pod. Pods consume node resources and PVCs consume PV resources. Pods can request specific levels of resources (CPU and Memory). Claims can request specific size and access modes (e.g., can be mounted once read/write or many times read-only).              
local persistentVolume example:     
[Configure a Pod to Use a PersistentVolume for Storage](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)  
should create a /mnt/data directory in node machine

## ClusterIP公开以下内容：
    A ClusterIP service is the default Kubernetes service.   
    It gives you a service inside your cluster that other apps  
    inside your cluster can access. There is no external access.

    If you can’t access a ClusterIP service from the internet, why  
     am I talking about it? Turns out you can access it using the Kubernetes proxy!

    $ kubectl proxy --port=8080

    Now, you can navigate through the Kubernetes API to access this service using this scheme:

    http://localhost:8080/api/v1/proxy/namespaces/<NAMESPACE>/services/<SERVICE-NAME>:<PORT-NAME>/

    So to access the service we defined above, you could use the following address:

    http://localhost:8080/api/v1/proxy/namespaces/default/services/my-internal-service:http/

## NodePort
    A NodePort service is the most primitive way to get external    
    traffic directly to your service. NodePort, as the name implies,   
    opens a specific port on all the Nodes (the VMs), and any    
    traffic that is sent to this port is forwarded to the service.

## LoadBalancer
    A LoadBalancer service is the standard way to expose a service to the internet. 

[Kubernetes NodePort vs LoadBalancer vs Ingress? When should I use what?](https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0)

## Labels和Selector
    Labels其实就一对 key/value ，被关联到对象上，标签的使用我们倾向于能够标示对象的特殊特点，并且对用户而言  
    是有意义的（就是一眼就看出了这个Pod是尼玛数据库），但是标签对内核系统是没有直接意义的。标签可以用来划分  
    特定组的对象（比如，所有女的），标签可以在创建一个对象的时候直接给与，也可以在后期随时修改，每一个对象可以  
    拥有多个标签，但是，key值必须是唯一的