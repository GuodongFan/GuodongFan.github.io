---
title: Word2vec
published: true
category: research
tag: Word2vec 
---

通过word2vec的学习，实现挖掘图中的信息.

我觉得学习新东西，最怕的是过早的进入细节.

## 架构图

![Architecture](http://plusnet.cn/assets/include/cbow.png)

## 算法
输入：基于CBOW的语料训练样本，词向量的维度大小M，CBOW的上下文大小2c,步长$\eta$

输出：霍夫曼树的内部节点模型参数θ，所有的词向量w

    1 基于语料训练样本建立霍夫曼树。

    2 随机初始化所有的模型参数θ，所有的词向量w

    3 进行梯度上升迭代过程，对于训练集中的每一个样本(context(w),w)做如下处理：

        a  e=0， 计算$x_w$=$\frac{1}{2c}\sum_{i=1}^{2c} x_i$
        b  for j = 2 to $l_w$, 计算：
                $f=\Simgma(x_w^T θ_{j−1}^{w})$
                $g=(1−d_j^w−f)η$ 
                $e=e+gθ_{j−1}^{w}$
                $θ_{j−1}^{w}=θ_{j−1}^{w}+gx_w$
        c 对于context(w)中的每一个词向量xi(共2c个)进行更新：
                $x_i$=$x_i$=e
        d 如果梯度收敛，则结束梯度迭代，否则回到步骤3继续迭代。