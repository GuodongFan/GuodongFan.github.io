---
title: Regional Multi-Person Pose Estimation 
published: true
category: review
tag: AlphaPose 
---
上海交大，卢策吾团队

## Some Concepts

Two-step framework: 首先，检测human bounding boxes. 然后，在每个bouding box的基础上estimate the pose.
精度受检测到的bounding boxes的质量影响.


Part-based framework: 首先，检测人体部件. 然后，将部件组装生成多人的pose.
当两个或两个以上的人太近时候，组装的人体pose模棱两可. 此外，由于仅仅利用了二阶身体部位依赖性，基于部分的框架失去了从全局姿势视图识别身体部位的能力。另外part-based 框架少了




