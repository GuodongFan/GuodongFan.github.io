---
title: Micro-service 
published: true
category: work
tag: Microservice
---

采用kubernetes进行服务部署和集群管理，采用istio处理服务通讯和治理.

## Service Mesh

服务网络是为了解决微服务的通信和治理而出现的一种架构模式.

通讯代理进程和应用进程一起部署，因此形象地把这种部署方式称为sidecar. 应用间所有流量都经过代理，由于代理以sidecar方式和应用部署在同一台主机上，应用和代理之间的通讯被认为是可靠的. 由代理来负责找到目的服务并负责通讯的可靠性和安全性等问题.

`服务网格`是一个基础设施层，用于处理服务间通信。云原生应用有着复杂的服务拓扑，服务网格保证请求可以在这些拓扑中可靠地穿梭. 在实际应用当中，服务网格通常是由一系列轻量级的网络代理组成的，它们与应用程序部署在一起，但应用程序不需要知道它们的存在.

## Kubernetes (k8s) 
Kubernetes是自动化容器操作的开源平台. 这些容器操作包括：部署、调度和节点集群间扩展.

具体功能：
1. 自动化容器部署和复制.
2. 实时弹性收缩容器规模.
3. 容器编排承租，并提供负载均衡.
4. 调度容器在哪个机器上运行.

![Architecture](http://plusnet.cn/assets/include/k8s_architecture.png)

![Architecture](http://plusnet.cn/assets/include/k8s_node.png)

![Architecture](http://plusnet.cn/assets/include/k8s_node2.png)