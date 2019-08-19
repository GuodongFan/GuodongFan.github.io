---
title: Learning to Adapt Structured Output Space for Semantic Segmentation 未看完
published: true
category: review
tag: TransferLearning
---

## Motivation

The trained model may not generalize well to unseen images, especially when there is a domain gap between the training (source) and test (target) images.

Most approaches tackle the problem by aligning the feature distribution between source and target images.

pixellevel domain adaptation problem in the output (segmentation) space.

## Approach

1. a segmentation model to predict output results.

2. a discriminator 判别器 to distinguish whether the input is from the source or targget segmentation output.

