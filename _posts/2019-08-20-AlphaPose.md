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

`The spatial transformer network (STN) has demonstrated excellent performance in selecting region of interests automatically.`


Mathematically, the STN performs a 2D affine transformation 仿射变换.

A spatial detransformer network (SDTN) is required to remap the estimated human pose back to the original image coordinate.

SDTN is an inverse procedure of STN.

$[\gamma_1 \gamma_2]=[\theta_1 theta_2]^{-1}$
$\gamma_3 -1 \times [\gamma_1 \gamma_2]\theta_3$

### Parallel SPPE

`To further help STN extract good human-dominant regions.` 


## Parametric Pose NMS

Human detectors inevitably generate redundant detections. Therefore, pose non-maximum suppression (NMS) is required to eliminate the redundancies. 

The pose $P_i$, with $m$ joins is denoted as {$<k_i^1, c_i^1>, ..., <k_i^m, c_i^m>$}, where $k_i^j$  and $c_i^j$ are the $j^{th}$ location and confidence score of joints respectively.


### Elimination Criterion 

`To define pose similarity in order to eliminate the poses which are too close and too similar to each other.`

Pose distance metric $d(P_i, P_j|\Lambda)$