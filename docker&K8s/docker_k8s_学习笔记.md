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

>**To work with Kubernetes objects–whether to create, modify, or delete them–you’ll need to use the Kubernetes API.**
