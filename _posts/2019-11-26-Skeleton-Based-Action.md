---
title: Spatial Temproal Graph Convolutional Networks for Skeleton-Based Action Recognition
published: true
category: review
tag: cv
---

Sijie Yan, The Chinese University of Hong Kong，AAAI2018.

## 问题
其他方法的缺点， 1. hand-crafted 手工特征 2. 没有分析关节点的关系。 

## 贡献

通过扩展Graph Neual Networks为Spatial-temporal Graph Model, called Spatial-Temporal Graph Convolutional Networks(ST-GCN). 

## 框架

### Skeletion Graph Construction
定义无向时空图$G=(V,E)$

$V=\{v_{ti}\|t=1,...,T, i=1,...,N\}$

The edge set $E$ is composed of two subsets.

$E_S=\{v_{ti}V_{tj}\|(i,j)\in H\}$

$E_F={v_{ti}v_{(t+1)i}}$

