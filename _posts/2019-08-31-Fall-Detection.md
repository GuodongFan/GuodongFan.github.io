---
title:  Fall Detection
published: true
category: work
tag: work
---

## 质心位置

$
X_{cent}=(x_l+x_r)/2 
$

$Y_{cent}=(y_t+y_b)/2$

## 人体宽高比

$R_{ratio}=W/H$

当人体保持直立时，其宽度远比高度小，外接框宽高比小于1。当人体躺下时，外接框的宽高比大于1.

## 我的思路


<div class="mermaid">
graph TB

A[YOLOv3检测目标]-->B(卷积神经网络fine-tune 跌倒识别)
B-->C(画出目标框及任务状态)

</div>