---
title: Automatic Scaling for Microservices with an Online Learning Approach
published: true
category: review
tag: Microservice
---
School of Data and Computer Science, Sun Yat-sen University, iCWS 2019

## Motivation

利用微服务自动扩展应对间歇及不可预测的负载以满足SLA的要求.


As the workload of one application in the Cloud is unpredictable, it is crucial to automatically scale out/in with resource as few as possible on condition that meeting the SLA requirements, in the face of workload changes .

## Some Concepts

service level agreement (SLA) 是在一定开销下为保障服务的性能和可靠性，服务提供商与用户间定义的一种双方认可的协定。通常这个开销是驱动提供服务质量的主要因素。

Service mesh is a dedicated (专用的) infrastructure layer for handling service-to-service communication. It is responsible for the reliable distribution of requests through the complex topology of micro services.

Istio is a completely open source service mesh that sits transparently on existing distributed applications and offers a complete solution to satisfy the diverse requirements (e.g., metrics collecting, request tracing) of micro-service applications. Istio,” https://istio.io, 2019, [Online; accessed 1-February-2019].

![Architecture](http://plusnet.cn/assets/include/Microscaler.png)
