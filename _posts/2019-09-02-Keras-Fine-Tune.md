---
title: Keras精调网络
published: true
category: work
tag: work 
---

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
