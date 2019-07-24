---
title: 训练YOLOv3
published: true
---

## 为什么选择YOLOv3
RCNN族，最先进的MASK RCNN速度太慢，不能满足real time。因此，在公司项目中选定YOLOv3做目标检测。

## 标注工具

MASK RCNN 用http://www.robots.ox.ac.uk/~vgg/software/via/via_demo.html这个网页进行标注即可。

YOLOv3没有延用一些标注标准，而是自己开发了个标注工具，yolo_mark。
