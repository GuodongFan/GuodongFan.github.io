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
当两个或两个以上的人太近时候，组装的人体pose模棱两可. 此外，由于仅仅利用了二阶(second order)身体部位依赖性，基于part-based framework失去了从全局姿势视图识别身体部位的能力。

## 概要

Aim to dectect accurate human poses even when given inaccurate bounding boxes. 

The framework consists of three componenets: Symmetric Spatial Transformer Network (SSTN).
Parametirc Pose Non-Maximum-Suppression (NMS). Pose-Guided Proposals Generator (PGPG).

## Symmetric STN and Parallel SPPE

### STN and SDTN

Mathematically, the STN performs a 2D affine transformation 仿射变换.

A spatial detransformer network (SDTN) is required to remap the estimated human pose back to the original image coordinate.

SDTN is an inverse procedure of STN.

$[\gamma_1 \gamma_2]=[\theta_1 theta_2]^{-1}$
$\gamma_3 -1 \times [\gamma_1 \gamma_2]\theta_3$

