---
title: Hybrid Method for Minimizing Service Delay in Edge Cloud Computing through VM Migration and Transmission Power Control
published: true
category: review
tag: review
---

IEEE Transaction on computers, Tiago Gama Rodrigues

## 词汇 
transmission power control 传输功率控制

Transmission Delay 传输延迟 lowering the time required for transmitting data between the user and the cloudlet

Processing Delay 处理延迟 d lowering the time spent by the cloudlet to process the request sent by the user

Poisson process 泊松过程 参考https://www.zhihu.com/question/26441147/answer/429569625
exponential distribution 指数分布 参考https://www.zhihu.com/question/24796044/answer/673838656


![Framework](http://plusnet.cn/assets/include/poisson_distribution.jpg)
## Processing Delay 
通过基于二项分布的泊松分布与指数分布，构建任务在边缘上的延迟，其中边缘每次可以执行K个VM service跑在VM上.


