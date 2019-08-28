---
title: Graph Neural Networks
published: true
category: research
tag: Graph Neural Networks
---

传统的机器学习应用，在处理阶段，将图结构映射为简单的表示，比如实向量，即将图结构进行压缩. 一些重要的信息可能会丢失，例如节点间的拓扑信息依赖.

世界上另一种数据表现形式是Non-Euclidean Domain，这类数据包括社交网络、蛋白质结构、交通网络等. 这类数据内部没有规则的grid结构，而是展现出一种多变的动态拓扑. 


一个模型的CG(Combinatorial Generalization) 取决于两点：

1. Structured representation & computation of the building blocks
2. Relational Inductive Bias (RIB) available in the model: RIB

因此，如何设计一个模型（blocks），使其具有structured representation，而且使其内部具有强的RIBs，而且让这个模型generally and uniformlly可以适应both Euclidean or Non-Euclidean数据，就是突破深度学习瓶颈的关键。

## 参考
Graph Neural Networks: A Review of Methods and Applications, Tsinghua University, Jie Zhou

Relational inductive biases, deep learning, and graph networks, DeepMind, Peter W. Battaglia