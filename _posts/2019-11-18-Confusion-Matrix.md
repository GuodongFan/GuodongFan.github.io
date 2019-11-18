---
title:  混淆矩阵
published: true
category: work
tag: work
---

![Framework](http://plusnet.cn/assets/include/confusion_matrix.png)

## 一级指标

四个指标：
1. 真实值是positive, 模型认为是positvie的数量。TP
2. 真实值是positive，模型认为是negative的数量。FN 这就是统计学上第一类错误（Type Ⅰ Error）
3. 真实值是negative，模型认为是positive的数量。FP 这就是统计学上第二类错误（Type Ⅱ Error）
4. 真实值是negative，模型认为是negative的数量。TN

## 二级指标
![Framework](http://plusnet.cn/assets/include/confusion_matrix_2.png)

## 三级指标

$F1-Score=\frac{2PR}{P+R}$, F1-Score指标综合了Precision与Recall的产出结果。F1-Score的取值范围0-1，1代表模型输出最好，0代表模型输出结果最差。

## 多分类
当分类问题是二分类，混淆矩阵可用上面的计算方法。当分类的结果用于多种分类时，混淆矩阵同样适用。