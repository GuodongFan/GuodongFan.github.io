---
title: Nash Equilibrium and Decentralized Pricing for QoS Aware Service Composition in Cloud Computing Environments
published: true
category: review
tag: Composition
---

## 基础

Orchestration：编制
Choreography：编排

WSO（Web Services Orchestration）定义了组成编制（orchestration）的服务，以及这些服务的执行顺序（比如并行活动、条件分支逻辑等）。因此，可以将编制（orchestration）视为一种简单的流程，这种流程自身也是一个Web服务。

WSC（Web Services Choreography）关注于定义多方如何在一个更大的业务事务中进行协作。WSC通过“各方描述自己如何与其他Web服务进行公共消息交换”来定义业务交互，而不是像WSO中那样描述一方是如何执行某个具体业务流程的。

## 解决的问题
服务组合的QoS 由参与组合的服务共同决定，因此，需要有效的机制来调节这些服务提供商以动态地和共同地决定服务组合方案，与用户建立SLA(Service Level Agreement)，以及在提供商之间划分收入。 本文从云计算环境中服务组合的经济方面，以解决动态建立灵活服务组合方案的定价问题。 每个基本服务提供商都可以具有战略性和自我激励。

## 符号

第i个基本服务提供者 $csp_i (i \in \lbrack 1,...,n\rbrack)$

第i个基本服务 $s_i$

$\omega=\lbrack(\overrightarrow{Q_1},...,\overrightarrow{Q_n}),(p_1,...,p_n)\rbrack$, $\overrightarrow{Q_i}$代表$S_i$的QoS;$p_i$代表价格;$p_i$是从用户的付款$p_u$拆分出来的.

服务提供商的利润 $f_i(x_i)=revenue_i(x_i, X_{-i})-cost_i(x_i)$, $X_{-i}$代表其他基本服务的响应时间.

reference service参考服务，构建每种类型服务的历史执行时间的常识。

##
