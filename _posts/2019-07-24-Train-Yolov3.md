---
title: 训练YOLOv3
published: true
category: work
tag: YOLO
---

## 为什么选择YOLOv3
RCNN族，最先进的MASK RCNN速度太慢，不能满足real time。因此，在公司项目中选定YOLOv3做目标检测。

## 标注工具

MASK RCNN 用http://www.robots.ox.ac.uk/~vgg/software/via/via_demo.html这个网页进行标注即可。

YOLOv3没有延用一些标注标准，作者自己开发了个标注工具，yolo_mark。ps:你用现有数据标准自己开发个工具多好，造福大众多好啊。

## 训练原因

YOLOv3可以识别的物体种类虽然比较多，本项目只需要识别出人就可以，并想通过YOLOv3识别出的行人，进行目标跟踪，实时的检测行人的运动状态。然而，在摔倒等过程中，提供的模型检测率并不好，因此需要加入行人的一些其他的状态去重新训练这个模型。
