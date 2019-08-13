---
title: Detecting Objects as Paired Keypoints
published: true
category: review
tag: Detection
---

CornerNet: Detecting Objects as Paired Keypoints Hei Law, Jia Deng

启发于自底向上的骨架检测算法.

## Anchor Box版本的缺点

anchor boxes 有两个缺点：1. 需要大量的anchor boxes，因为检测器区分是否每个anchor box有效的覆盖一个ground truth box，并且很多的anchor box要求确保覆盖大部分的ground truth boxes. 最后，就只有一小部分anchor boxes会与ground truth重叠，这就导致了正负样本的不平衡，减慢了训练速度. 2. anchor boxes引入了很多超参和设计选择. 包括多少个box，它的大小及宽高比.

## 创新点

将目标检测看作一对关键点——左上角和右下角. 使用单个个卷积神经网络去预测同一类所有实例的的左上角热力图，右下角的热力图，及一个对于每个检测角的嵌入的向量. 嵌入的向量用于对属于同一个目标的一对角点进行分组.

corner pooling, 边界框的一角通常在目标之外， 角点不能根据当前的信息进行定位. 为了确定像素位置是否有左上角，我们需要水平向右的看目标的最上面边界（寻找水平方向的极大值），并且从垂直方向向底看目标最左边的边界.  由此设计了两个方向的max-pooling. `这种引入人为的特征其实不能算优势，也可能影响精度`

为什么detecting corner 有效？ 1. box的中心很难去定位，因为它需要物体的四个边, corner只需要两个, 并且使用cornor pooling. 2. corners 提供了更有效的方法来密集离散化box的空间： 使用$O(wh)$的corner去表达$O(w^2h^w)$个可能的anchor boxes.


## Overview



### 检测corner
$2\times C\times H\times W$

削弱惩罚 $e^{-\frac{x^2+y^2}{2\sigma ^2}}$

$P_{cij}$

### 对corner分组
灵感来源于multi-person pose estimate.

左上角和右下角的embedding距离应该比较小. (？有的物体比较大，有的比较小)

### Corner Pooling

### Hourglass Network (backbone)
