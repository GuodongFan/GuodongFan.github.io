---
title: Diversified Quality Centric Service Recommendation
published: true
category: review
tag: Recommendation
---

ICWS, Anhui University, 2019

## Motivation

服务的推荐帮助用户找到合适的服务，客户对不同质量维度的偏好的相关性使得服务推荐成为更复杂的问题. `ps:这和服务排名有些相似啊,两者的共同点与不同点是什么？` 建模质量相关性具有挑战性，因为对于客户而言，多维质量相关性进行公式化或数字化指定通常过于苛刻(too demanding)。

Skyline 的缺点：the number of dynamic skyline services can be excessive.

首先计算skyline服务,然后使用k-means对$S_{DSL}$聚类，最后DQCSR根据聚类中心或覆盖区域从每个cluster选择一个服务，生成最后的推荐结果.


## Some Concepts

Mutually-substitutable services differ from each other by their non-functional properties.


Foure categories: 1. utility-based 2. skyline-based 3. collaborative filter based 4. matrix factorization based

representativeness and diversity: 1. representativeness requires that for any service in the recommendation results there must not be any other services that are more similar to customer’s quality preference in terms of all quality dimensions. 2. Diversity takes a step further by requiring that the recommendation results should include services that are representative in as many quality dimensions as possible.

![Architecture](http://plusnet.cn/assets/include/fcos_architecture.png)
