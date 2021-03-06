---
title: 一种综合考虑主客观权重的 Web 服务 QoS 度量算法
published: true
category: review
tags: ranking QoS
---
马友, 王尚广, 孙其博, & 杨放春, 软件学报(2016)

## 解决的问题
已有的Web服务QoS度量方法无法对用户偏好得模糊性予以准确量化.其次,候选服务QoS属性数据分布特征的忽视,导致度量结果不准确.

## 文章贡献

自适应用户偏好的主观权重计算方法,和服务潜能保障的客观权重计算方法.
引入了粗糙集.

## 问题演示

服务|$p_1$|$p_2$|$p_3$|$p_4$|$p_5$
-|-|-|-|-|-
$ws_1$|2|2|8|7|4
$ws_2$|2|1|8|6|6
$ws_3$|2|1|8|9|5
$ws_4$|2|2|8|10|3

每个服务在属性$p_1$和$p_3$上具有相同的取值,若用户偏好考虑的属性为$p_1$,$p_2$及$p_3$,根据已有方法,会导致QoS度量结果只取决于$p_3$.


## SWDM主观权重计算

1. 首先根据不同QoS属性在用户体验中的不同敏感度将偏好属性划分层次.
2. 基于划分的层次及敏感参数$\beta$建立主观权重分配约束条件,通过该条件计算主观权重.

将用户偏好下进行QoS度量的WS记为S=(WS, A, P), 其中所有服务组成的集合为WS,所有服务属性组成的集合记为A,将用户偏好涉及的属性集合记为P($\subseteq$A),将主要偏好涉及的属性记为$P_f$($\subseteq$A),将次要偏好涉及的属性集合记为$P_s$($\subseteq$A),且$P_f\cap P_s=\emptyset$,$P_f\cup P_s=P$.


基本思想为,同一层次对于用户的重要程度相同,敏感参数$0\leq\beta\leq 1$反映了次要偏好对主要偏好的占比.

`虽然东西比较low,但形式化做的不错`.

## OWDM客观权重计算

通过分析QoS属性数据的分布特征,合理地评价各QoS属性在QoS度量中的作用,进而确定具有实际意义的客观权重.

服务|$p_1$|$p_2$|$p_3$
-|-|-|-
$ws_1$|2|2|1
$ws_2$|2|1|2
$ws_3$|2|1|3
$ws_4$|2|2|4

$p_1$属性视角下,服务不可分辨;$p_2$下有2组不可分辨;$p_3$都可分辨.

客观权重的计算使用文章-知识的粒度计算及其应用_苗夺谦,中的方法.

定义 1. 称$I=(U,A,V,f)$为一个信息系统,其中,$U$为论域,是非空有限对象集;$A$为非空有限的属性集合;对于$a\in A$, $V_a$是$a$的值域,且$V=\bigcap_{a\in A}V_a$;$F:U\times A\to V$成为信息函数,使得对每一$A\in A, u\in U$,都有$f(u,a)\in V_a$.

定义 2. 对于任一$X\subseteq A$,定义$X$上的不可分辨关系$I_x$为$I_x=\{(x,y)\in U\times U \| \forall a\in X, f(x,a)=f(y,a)\}$

定义 3. 设$I=(U,A)$为一个信息系统,$X\subseteq A$, $I_x$为定义在$X$上的不可分辨关系,$I_x$也称为知识,知识$I_x$的粒度定义为$GD(I_x)=\|I_x\|/\|U^2\|=\|I_x\|/\|U\|^2$

定义 4. 设$I=(U,A)$为一个信息系统,$X\subseteq A,x\in A$.$x$对于$X$的重要程度,即在$X$中增加属性$x$后知识粒度的减小程度,记为
$SIG_X(x)=\frac{GD(X)-GD(X\cup x)}{GD(X)}=1-\frac{I_{X\cup x}}{I_X}$

定义 5. 设有服务集$S=(WS,A,P)$,对$\forall p \in A$,定义属性$p$的参考度为其对$WS$中不同服务的区别能力,记为$REF(p)=SIG_\emptyset (P)=1-\|I_p\|/ \|WS\|^2$

定义 6. 设有服务集$S=(WS,A,P)$,定义属性p(\in A)的客观群众为 $ow(p)=REF(p)/\sum_{p\in A}REF(p)$

定义 7. 设有服务集$S=(WS,A,P)$,若$OQ(ws^x)=max\{OQ(ws)\|ws\in WS \}$,则称$ws^x$为$WS$中整体性能最佳的服务.其中,$OQ(ws)=\sum_{p\in A} nv_{ws}(p).ow(P)$表示服务$ws$的客观QoS, $nv_{ws}(p)$表示服务$ws$在属性$p$上的归一化取值.

`和熵权法类似`。
