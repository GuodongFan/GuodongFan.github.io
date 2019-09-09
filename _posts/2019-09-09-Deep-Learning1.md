---
title: 深度学习遇到的问题
published: true
category: work
tag: work
---

## feature map与filter的关系

上一层输出64个featuremap ，下一层的filter 的channel 就会变为64，一个filter做卷积的话将会在64个featuremap组成的64channel上做，如果有128个filter，将再次生成128个featuremap，而不是128*64.

## batchsize的影响

batch的选择决定下降的方向. 比如数据集比较校，完全可以采用全数据集（Full Batch Learning）的形式，有两个好处：1. 由全数据集确定的方向能够更好地代表样本总体，从而更准确地朝向极值所在的方向. 2. 由于不同权重的梯度值差别很大，因此选取一个全局的学习率很困难。Full batch learning 可以使用rprop只基于梯度符号并且针对性单独更新个权值. 

大数据集，反而上面的两个好处变为两个坏处：1. 随着数据集的海量增长和内存限制，一次性载入所有的数据进来变得越来越不可行. 2. 以rprop的方式迭代，会由于各个batch的采样差异性，各次梯度修正值相互抵消，无法修正。这才有了rmsprop的妥协方案.

如果每次只训练一个样本，即batch_size = 1. 这就是在线学习. 使用在线学习，每次修正方向以各自样本的梯度方向修正，横冲直撞各自为政，难以达到收敛. 

选择一个适中的Batch_Size值, 这就是批梯度下降法（Mini-batches+Learning）. 因为如果数据集足够充分，那么用一半（甚至少得多）的数据训练算出来的梯度与用全部数据训练出来的梯度是几乎一样的. 

合理范围内，增大batch_size的好处：1. 内存利用率提高，大矩阵乘法的并行化效率提高. 跑完一次epoch（全数据集）所需迭代次数减少，对于相同数据量的处理速度进一步加快. 2. 在一定范围内，一般来说batchsize越大，其确定的下降方向越准，引起训练震荡越小. 

盲目增大batchsize的坏处：1. 内存利用率提高了，但是内存容量可能撑不住了. 2. 跑完一次 epoch（全数据集）所需的迭代次数减少，要想达到相同的精度，其所花费的时间大大增加了，从而对参数的修正也就显得更加缓慢。 Batch_Size 增大到一定程度，其确定的下降方向已经基本不再变化.

## Dropout

dropout可以放在很多类层的后面，用来抑制过拟合现象，常见的可以直接放在Dense层后面，对于在Convolutional和Maxpooling层中dropout应该放置在Convolutional和Maxpooling之间，或Maxpooling后都可.

## L1或L2正则化系数

L1范数：为x向量各个元素绝对值之和

L2范数：为x向量各个元素平方和的1/2次方。（又称Eudclidean范数）

```
C1 = Convolution2D(20, 4, 4, border_mode='valid', init='he_uniform', activation='relu',W_regularizer=l2(regularizer_params))
```

对于过拟合有着不错的效果，在一定程度上提升了模型的泛化能力.

```
keras.layers.normalization.BatchNormalization(epsilon=1e-06, mode=0, axis=-1, momentum=0.9, weights=None, beta_init='zero', gamma_init='one')
```

mode: 整数，指定规范化的模式，取0或1.

0：按特征规范化，输入的各个特征图将独立被规范化. 规范化的轴由参数axis指定。注意，如果输入是形如（samples，channels，rows，cols）的4D图像张量，则应设置规范化的轴为1，即沿着通道轴规范化.

1：按样本规范化，该模式默认输入为2D.

我们大都使用的都是mode=0也就是按特征规范化，对于放置在卷积和池化之间或之后的4D张量，需要设置axis=1，而Dense层之后的BN层则直接使用默认值就好了.






