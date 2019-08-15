---
title: Cuckoo Optimization Algorithm
published: true
category: review
tag: Optimization
---

Cuckoo Optimization Algorithm, Ramin Rajabioun, Applied Soft Computing, sci 2区

## Motivation

适合非线性优化问题的算法.

## Algorithm

Habitat. In a $N_var$-dimentional optimization problem, a habitat is an array of $1\times N_{var}$, representing current living position of cuckoo.

habitat = [$x_1, x_2, ..., x_{Nvar}$]

每个变量的值($x_1, x_2, ..., x_{Nvar}$)是浮点型数字. The profit of a habitat is obtained by evaluation of profit function $f_p$ at a habitat ($x_1, x_2, ..., x_{Nvar}$).

profit = $f_p(habitat)=f_p(x_1, x_2, ..., x_{Nvar})$

profit = $-Cost(habitat)=f_c(x_1, x_2, ..., x_{Nvar})$

Rgg laying radius (ELR)

ELR = $\alpha \times \frac{\mbox{Number of current cuckoo's eggs}}{\mbox{Total number of eggs}} \times (var_{hi}-var_{low})$

$\alpha$ is an integer, supposed to handle the maximum value of ELR.

Only one egg in a nest has the chance to grow.

![Architecture](http://plusnet.cn/assets/include/cuckoo_algorithm.png)
