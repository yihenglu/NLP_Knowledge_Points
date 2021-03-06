# 机器学习总述

tags: 机器学习

---



![贝叶斯](..\img\贝叶斯\贝叶斯.png)

[TOC]

## 1. 频率派 vs 贝叶斯派

对于有 n 个样本的样本集 $X = (x_1, ..., x_n)$ 以及参数 $\theta$， 那么有 $X$ 服从概率分布 $ P(x|\theta)$ 

### 频率派

**频率派**认为 $\theta$ 是一个未知的常量， 数据 $X$ 是一个随机变量，其服从一定的概率分布， 目的是通过极大似然估计 + 随机变量 $X$ 来估计出未知参数 $\theta$ 。 
$$
\theta_{MLE} = argmax_{\theta} \,\, log P(X|\theta)
$$

### 贝叶斯派

贝叶斯派认为 $\theta$ 是一个随机变量，其服从一定的概率分布 $p(\theta)$。其采用最大后验估计来计算 $P(\theta|X)$。
$$
P(\theta|X) = \frac{P(X | \theta) P(\theta)}{P(X)}
$$

- 先验： $P(\theta)$ ， 似然： $P(X|\theta)$ ， 后验：$P(\theta|X)$

$$
\theta_{MAP} = argmax_{\theta} \,  \, P(\theta | X) = argmax_{\theta} P(X|\theta)P(\theta)
$$



## 2. 极大似然估计 vs 最大后验估计

### 1.  极大似然估计 - MLE

- 原理：利用已知的样本结果，反推最有可能（最大概率）导致这样结果的参数值。

- 极大似然估计提供了一种给定观察数据来评估模型参数的方法：**模型已定，参数未知**。经过若干次实验，观察结果，利用实验结果得到某个参数值能够使得样本出现的概率为最大，称为极大似然估计。

- 离散情况下参数 $\theta$ 的似然函数：

  > $$
  > L(\theta) = L(X_1, X_2, \cdots, X_n; \theta) = \prod_{i=1}^n p(X_i| \theta)
  > $$
  >

- **极大似然估计：** 对于给定的样本值$(x_1, x_2, \cdots, x_n)$ 有：
  $$
  \hat{\vec\theta}= \mathop {\arg \max}_{\vec\theta} L(\vec\theta )
  $$

- 使得似然函数 $L(x_1, x_2, \cdots, x_n; \theta)$达到最大值的参数值 $\hat{\theta} = \hat{\theta} (x_1, \cdots, x_n)$ 称为未知数 $\theta$ 的最大似然估计值。

### 2. 最大后验估计 - MAP

MAP 的基础是贝叶斯公式：
$$
贝叶斯估计：P(\theta|X) = \frac{P(X | \theta) P(\theta)}{P(X)}= \frac{P(X | \theta) P(\theta)}{\int_{\theta} P(X|\theta)P(\theta)d{\theta}} \\
贝叶斯预测：p(\hat{x} | X) = \int_{\theta} p(\hat{x},\theta|X) d{\theta} = \int_{\theta} p(\hat{x}|\theta) p(\theta|X)d{\theta}
$$
MAP 优化的就是后验概率， 目的是通过观测值使得后验概率最大：
$$
\theta_{MAP} = argmax_{\theta} \,  \, P(\theta | X) = argmax_{\theta} P(X|\theta)P(\theta)
$$



---

## QA

### 1. 极大似然估计与最大后验概率的区别？

- 最大似然估计提供了一种给定观察数据来评估模型参数的方法， 最大似然估计中的采样满足**所有采样都是独立同分布的假设。**
- 最大后验概率是根据经验数据获难以观察量的点估计,与最大似然估计最大的不同是最大后验概率融入了要估计量的先验分布在其中，所以最大后验概率可以看做规则化的最大似然估计。

### 2. 概率与似然的区别

- 概率是指在给定参数$\theta$的情况下,样本的随机向量 $X=x$ 的可能性。
- **似然表示的是在给定样本 $X=x$ 的情况下,参数 $\theta$ 为真实值的可能性。**

一般情况,对随机变量的取值用概率表示。而在非贝叶斯统计的情况下,参数为一个实数而不是随机变量,一般用似然来表示。

### 3. 贝叶斯派与频率学派的区别

- 频率派认为抽样是无限的,在无限的抽样中,对于决策的规则可以很精确。贝叶斯派认为世界无时无刻不在改变,未知的变量和事件都有一定的概率,即后验概率是先验概率的修正。
- 频率派认为模型参数是固定的,一个模型在无数次抽样后,参数是不变的。而贝叶斯学派认为数据才是固定的而参数并不是。
- 频率派认为模型不存在先验而贝叶斯派认为模型存在先验。