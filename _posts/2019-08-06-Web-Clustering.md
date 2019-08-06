---
title: Relationship Network Augmented Web Services Clustering
published: true
category: review
tag: Clustering
---
ICWS

## 解决的问题

传统的方法基本上是通过服务特征的语义距离去聚类. 从WSDL中学习到潜在的主题，测量服务之前内容的相似性.
几乎没有工作利用在使用服务期间生成的结构化信息(服务组合和标记行为).
丰富的网络关系本质的反映了服务之间的正向或者负向的分类相关的信息，成为服务之间功能性近似性的强大补充.

`通过WSDL的语义信息及组合信息进行聚类`

## 符号

G=(V, E), V是服务的集合，$e_{i,j}=(v_i, v_j)\in E$是边， $e_{i,j}=1$ 是正向的边， $e_{i,j}=-1$是负向的边.

`本文中如果两个服务组合在一起，那么就会给负向的标志`

## 实现

![Architecture](http://plusnet.cn/assets/include/web_clustering.png)

1. Doc2Vecc
2. SiNE, 已建立好了服务之间的关系

描述服务的字符序列$v_i$为{ $w_1, ..., w_n $}