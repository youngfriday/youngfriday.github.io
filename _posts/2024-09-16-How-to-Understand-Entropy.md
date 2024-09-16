---
title: How to Understand Entropy
author: young
date: 2024-09-16 12:45:00 +0800
categories: [Math, AI]
tags: [Entropy]
math: true
---

# How to Understand Entropy

## Context

其实我一直对entropy这个概念一知半解的，我能背下来各种熵的形式，就比如熵、交叉熵、相对熵（KL散度），但想不明白为啥这样就能描述一个信息量的大小了（原谅弱小无知的我不能理解Shannon老爷子的伟大之处）。正巧人工智能课程布置了关于熵有关的作业，我也就借此机会把这个坑填上。

## About Entropy

### Information Content (Self-information)

$$
I(x) = -\log_b P(x)
$$

其中，$b$是对数的底数，通常为 2（bit）或 $e$（纳特）。一般省略$b$不写时认为是2。

- 当事件 $x$的概率 $P(x)$ 很小时，信息量 $I(x)$ 会较大，表示事件发生是非常“出乎意料”的，因此信息量很大。
- 当事件 $x$ 的概率 $P(x)$ 很大时，信息量 $I(x)$ 会较小，表示事件发生是比较“预料之中”的，因此信息量较少。

确定性事件的信息量是0。

### Entropy

$$
H(P) =E(I(x))= - \sum_{x \in X} P(x) \log P(x)
$$

事实上，熵就是信息量的期望值，对于确定性事件，有$P(x)=1$，此时熵最小为0；而对于等概率事件，$P(x)=\text{const}$，此时熵最大。

#### How to Understand

如果将熵的形式改写为：


$$
H(P) =  \sum_{x \in X} P(x) \log {\frac{1}{P\left( x \right)}}= \sum_{x \in X} P(x) I(X)
$$

将$\log {\frac{1}{P\left( x \right)}}$理解为确定一个事件所需要的bit数，比如一个袋子里面有8个球，其中7个是白球，剩下1个是黑球。那么随机摸到一个球是黑球的概率就是$\frac{1}{8}$。我们此时需要最快地找到黑球，那使用二分法，每次将球分成一半，留下有黑球的一半，$8\rightarrow 4 \rightarrow 2 \rightarrow 1$，可见最终需要$\log _28=3$次即可确定黑球。我们认为 $\log {\frac{1}{P\left( x \right)}}$ 即是确定对应颜色球所需要的操作次数，此时乘上对应的 $P(x)$ 求和就是确定所有颜色球所需次数的期望，称之为熵。

这部分的具体理解方式可以参考  [Peiwen-如何通俗的解释交叉熵与相对熵？](https://www.zhihu.com/question/41252833/answer/195901726) 

### Cross-Entropy

$$
H(P, Q) = - \sum_{x \in X} P(x) \log Q(x)
$$

其中，$P(x)$ 是真实分布，表示事件 $x$ 发生的真实概率；$Q(x)$ 是预测分布，表示模型预测事件 $x$ 发生的概率。

交叉熵度量的是使用分布 $Q$ 编码实际分布 $P$ 所需的平均比特数。它包含了两个部分：用 $Q$ 编码 $p$ 的代价，以及因 $Q$ 与 $P$ 不一致所带来的额外代价。

#### How to Understand

这里可以使用上面在Entropy中模球的理解方式，无非就是现在的摸球次数变为 $\log {\frac{1}{Q\left( x \right)}}$，显然由于 $Q(x)$ 不准确的缘故，这个摸球次数显然是不准确的，整体意义上势必会带来摸球次数期望的增加。

还有一个比较巧妙的理解方式，来源<https://www.zhihu.com/question/65288314/answer/849294209>，当然我对答主的表述方式做了一些改进，以使得其更准确更好理解。

我们可以从$MLE$（极大似然估计）的角度来理解。现在有一个变量 $x$ ，我们对它的模型预测分布为 $Q(x)$ ，我们就对它做 $N$ 次独立同分布的实验（我们让 $N\rightarrow \infty $），对应 $x$ 的观测次数为 $N(x)$ 。如此一来，它的似然值即可写成：


$$
L=\prod_x^{}{Q\left( x \right) ^{N\left( x \right)}}
$$

取对数，为了统一形式，我使用 $\log$


$$
\log L=\sum_x^{}{N\left( x \right) \log Q\left( x \right)}
$$

然而，这个式子还有两个缺点，第一它是个负数，第二，它的数值和样本数量有关，所以我们进行归一化并取相反数，由于 $N\rightarrow \infty$ ，由大数定律，$P(x)$即为真实概率值，此时的形式已经和交叉熵一样了：


$$
-\sum_x^{}{\frac{N\left( x \right)}{N}\log Q\left( x \right)}=-\sum_x^{}{P\left( x \right) \log Q\left( x \right)}
$$

因此可以看出，交叉熵最小的实质就是似然值最大，可以证明，当交叉熵最小时一定有 $Q(x)=P(x)$ ，使用拉格朗日乘子法：


$$
W=-\sum_x^{}{P\left( x \right) \log Q\left( x \right)}+\lambda \left( \sum_x^{}{P\left( x \right)}-1 \right)
$$

对 $P(x)$ 求偏导得：


$$
-\frac{P\left( x \right)}{Q\left( x \right)}+\lambda =0
$$

即 $P(X)$ 与 $Q(x)$ 对应成比例，而又由二者的归一化条件得 $Q(x)=P(x)$ 时取得极大似然，也是最小交叉熵。

#### Binary Cross-Entropy

在二分类问题中，对于一个样本来说，真实标签 $x$ 只有两种可能：

- 当 $x=1$ 时，$P(1)=1,P(0)=0$
- 当 $x=0$ 时，$P(1)=0,P(0)=1$

模型的输出 $\hat{x}=Q(1)$ 表示预测结果 $x=1$ 的概率，则 $1-\hat{x}=Q(0)$ 表示预测结果 $x=0$ 的概率。


$$
% \begin{equation}\begin{split}
H(P, Q) = - \sum_{x=0,1} P(x) \log Q(x)\\\\
=-[P(1)\log Q(1)+P(0)\log Q(0)]\\\\
=-[P(1)\log{\hat{x}}+P(0)\log{(1-\hat{x})}]\\\\
=-[\hat{x}\log{\hat{x}}+(1-\hat{x})\log{(1-\hat{x})}]
% \end{split}\end{equation}
$$


此处最后一步的化简对应二分类的两种情况，分类讨论即可看出，两项中总有一项会等于0。

### Relative-Entropy (KL Divergence)

$$
D_{KL}(P || Q) = \sum_{x \in X} P(x) \log \frac{P(x)}{Q(x)}
$$

- **信息增益**：KL散度可以理解为使用分布 $Q$ 来近似分布 $P$ 时，所增加的平均信息量。它表示在这种不完美的近似中，描述真实事件所需的额外“开销”。
- **不对称性**：KL散度是一个**非对称**度量，意味着 $D_{KL}(P||Q) \ne D_{KL}(Q || P)$。这表明用 $P$ 近似 $Q$ 与用 $Q$ 近似 $P$ 的结果是不同的。

#### How to Understand

理解了上面的熵和交叉熵的概念，关于KL散度的理解也就迎刃而解了。

不难看出：


$$
H\left( P,Q \right) =H\left( P \right) +D_{KL}\left( P||Q \right)
$$

- $H(P)$ 是真实分布的熵，表示用分布 $P$ 编码数据的最小信息量
- $D_{KL}\left( P||Q \right)$ 表示使用 $Q$ 而非 $P$ 编码数据时，额外增加的信息量

KL散度可以被看作是衡量两个分布相似性的一种方法，但它**并不是一个对称的距离度量**。例如，如果我们用 $Q$ 来逼近 $P$，那么KL散度就会告诉我们：从 $P$ 转到 $Q$ 会损失多少信息。若 $P$ 和 $Q$ 越相似，KL散度越小；**当 $P$ 和 $Q$ 完全一致时，KL散度等于 0**。

# Reference

1. [Peiwen-如何通俗的解释交叉熵与相对熵？](https://www.zhihu.com/question/41252833/answer/195901726)  <https://www.zhihu.com/question/41252833/answer/195901726>
2. [灵剑-为什么交叉熵（cross-entropy）可以用于计算代价？](https://www.zhihu.com/question/65288314/answer/849294209)   <https://www.zhihu.com/question/65288314/answer/849294209>



