---
title: Network Embedding
published: true
category: Learning
tag: Embedding Deepwalk 
---

将数据转换为网络表示和从网络种提取潜在表示所面临的挑战.

## 网络潜入(网络节点表示，Network Embedding)

网络表达学习本质上是将网络进行降维从而更好得利用其它模型来处理网络数据。对于一个网络G=(V,E)来说，网络表达的结果是将这个网络变成维度为|V|xd的一个二维矩阵，|V|是指网络节点个数，d是每个节点表达的维度。网络表达学习相当于一个映射函数，将每个节点映射到一个向量中去。


### Graph Embedding v.s. Network Embedding

Graphs exists in mathematics. (Data Structure)
Mathematical structures used to model pairwise relations between objects.

Network exist in the real world. (Data)
Social network, logistic network, biology network, transaction network, etc.

### Structed-preserved network embedding

How to define neighborhood in networks? Deepwalk.

Deepwalk preserve social relation in vector space.

### High-Order Proximity

Solve the sparsity problem of network connnections.

Measure indirect relationship between nodes.

## Deepwalk

 深度游走算法是近年来第一个有影响力的大规模网络表达学习算法，它的本质是将随机游走（Random Walk）和自然语言处理中的skip-gram算法作组合所产生的算法.将在一个网络上随机游走的路径等同于一句自然语言.通过一定策略将游走的所有路径组合在一起当做是语料库.然后就可以用自然语言处理技术来进行网络表示学习.

### 随机游走（Random Walk）

随机游走是一个非常基础的基于网络的算法.它的本质就是从一个节点出发，随机选择它的一个邻接点，再从这个邻接点出发到下一个节点，重复这个步骤然后记录下所经过的所有节点.这个算法的变种在Google搜索和金融领域应用广泛.通过随机游走我们可以得到从每个节点出发的一条路径，`这条路径就代表了这个节点的结构信息`.

### Skip-gram算法

它是用一个词来预测这个词前后可能会出现哪些词.

### 深度游走算法

短的随机游走路径=句子.

由于网络的节点数目可能达到百万甚至千万级，节点的one-hot编码会过于稀疏，不同于传统的skip-gram模型直接用softmax函数得到输出，deepwalk采用的是层级softmax方法.

![Architecture](http://plusnet.cn/assets/include/deepwalk_hierachical.png)

一个优秀的方法是要建立在前人工作的基础上而不是凭空产生，并且当前最热门的问题并不一定是最值得研究的，冷门的问题也有其潜在的研究价值.

## 相关论文

A Tutorial on Network Embeddings, Stony Brook University, Haochen Chen

DeepWalk: Online Learning of Social Representations, Stony Brook University, Bryan Perozzi

Representation Learning for Attributed Multiplex Heterogeneous Network, Tsinghua University, Yukuo Cen