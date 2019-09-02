---
title: Keras制作自己的数据集并精调网络
published: true
category: work
tag: work 
---

`input shape`不指定各种问题.



## 制作数据集

导入图片，图片格式是RGB 60*160 png.

单张图片灰度化和导入使用PIL (opencv也可以)。
需要导入整个样本库，所以需要用append函数把新的单张图片矩阵加到整个矩阵集合里，这之前当然要定义一个数组来作为集合，如images = []。

之后再使用X = numpy.array(images)，这样便得到了numpy格式的数据集。

导入完毕后，我们可以通过print(X.shape)看看导入是否正确，例如我们导入了30000张60*160的图片，应得到：（30000, 60, 160）


## 精调网络
```
# 设置所有层trainable=False
for layer in model.layers:
    layer.trainable = False
# 或者使用如下方法冻结所有层
# model.trainable = False 
# 设置最后六层trainable=True
model.layers[-1].trainable = True
model.layers[-2].trainable = True
model.layers[-3].trainable = True
model.layers[-4].trainable = True
model.layers[-5].trainable = True
model.layers[-6].trainable = True
```

第一种冻结了，就没法再设置True了

```
# 可训练层
for x in model.trainable_weights:
    print(x.name)
print('\n')

# 不可训练层
for x in model.non_trainable_weights:
    print(x.name)
print('\n')
```
