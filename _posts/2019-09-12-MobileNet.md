---
title: MobileNet
published: true
category: review
tag: deep learning
---

## 定义

参数数量（params）：关系到模型大小，单位通常为M，通常参数用 float32 表示，所以模型大小是参数数量的 4 倍

理论计算量（FLOPs）：

是 floating point operations 的缩写（注意 s 小写），可以用来衡量算法/模型的复杂度，这关系到算法速度，大模型的单位通常为 G，小模型单位通常为 M

通常只考虑乘加操作(Multi-Adds)的数量，而且只考虑 CONV 和 FC 等参数层的计算量，忽略 BN 和PReLU 等等。一般情况，CONV 和 FC 层也会 忽略仅纯加操作 的计算量，如 bias 偏置加和 shotcut 残差加等，目前技术有 BN 的 CNN 可以不加 bias

## 计算公式

假设卷积核大小为$K_h \times K_w$，输入通道数为$C_{in}$，输出通道数为$C_{out}$，输出特征图的宽和高分别为 $W$和$H$，这里忽略偏置项

CONV标准卷积层：

params:$K_h \times K_w \times C_{in} \times C_{out}$

FLOPs: $K_h \times K_w \times C_{in} \times C_{out} \times H \times W = params \times H \times W$

FC全连接层：相当于K=1

params:$C_{in} \times C_{out}$

FLOPs:$C_{in} \times C_{out}$

## MobileNetV1

### 深度可分离卷积

depthwise 卷积时只使用了一种维度为in_channels的卷积核进行特征提取（没有进行特征组合）

pointwise 卷积只使用了output_channels 种 维度为$in\_channels 1\times 1 $的卷积核进行特征组合，普通卷积不同 depth 层的权重是按照 1:1:1…:1的比例进行相加的，而在这里不同 depth 层的权重是按照 不同比例(可学习的参数) 进行相加的

参数数量由原来的$p1 = F \times F \times in\_channels \times output\_channels$ 变为了$p2 = F \times F\times in\_channels\times 1 + 1\times 1\times in\_channels\times output\_channels$

## MobileNetV2

V2再depthwise卷积之前新加了一个pointwise卷积，可以提升维度。

![Architecture](http://plusnet.cn/assets/include/MobileNet.png)

## 参考

https://zhuanlan.zhihu.com/p/33075914

https://zhuanlan.zhihu.com/p/80041030