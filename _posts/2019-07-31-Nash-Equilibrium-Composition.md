---
title: Nash Equilibrium and Decentralized Pricing for QoS Aware Service Composition in Cloud Computing Environments
published: true
category: review
tag: Composition
---
ICWS

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

reference service参考服务，构建每种类型服务的历史执行时间的常识.

$1-\lambda$表示并行度.


## 收入按比例分配

每个提供商向云代理提出投标，以提供基本服务作为提供给最终用户的组合服务的一部分，然后根据特定的`收入分配机制`将用户支付分成参与的提供商.

$x=(x_1, ..., x_n)$, $x_i$代表服务商声明的相应时间.

每个供应商都要最大化其利润.

每个提供商的利润划分为，基础收款和额外收款. 其中额外收款不仅仅和自身的QoS有关还和其他提供商的QoS有关. 这样就构成一个非合作性博弈(零和游戏吧)

## 最优化

$\max \limits_{x_i \in X_i} f_i(x_i;X_{-i})$

存不存在使所有提供者都满意的服务组合？即达到纳什均衡.

## 纳什均衡

定义. 服务执行时间的出价向量$X=(x_1,...,x_n)$是非合作性博弈的纳什均衡，如果对于每个服务提供者$csp_i$($\forall i \in \mathrm{N}$)，$f_i(x_i;X_{-i})\ge f_i(i_i^{'};X_{-i})$, $\forall x^{'} \in X_i$.

## 怎样达到纳什均衡

通过解决Karush Kuhn Tucker（KKT）条件，找到其一阶必要条件的解决方案.

$f_i^{'}(x_i;X_{-i})=0$

## Dicentralized 方法

但是，要求提供者披露其利润函数是不切实际的，这通常是私人信息. 因此，服务提供商最好能够以分散的方式自行达到平衡. 为了解决这个问题，开发了一种分散的方法，每个服务提供商在每一轮中递归出价以最大化自己的利润. 在算法中，云代理负责管理递归出价过程.
