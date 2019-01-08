---
title: 机器学习1-基本概念
date: 2018-12-02 21:04:26
tags: 机器学习
---

### 符号说明

$ \mathcal{X} $                          样本空间或状态空间 
$ \mathcal{D} $                          概率分部 
$ D $                          数据样本(数据集)
$ \mathcal{H} $                          假设集
$ \mathfrak{L} $                           学习算法
$ {‖\cdot‖}_{p} $                  $ {L}_{p} $范数,$ p $缺省时为$ {L}_{2} $范数
$ \mathbb{E}_{\cdot \sim \mathcal{D}}[f(\cdot)] $           函数$ f(\cdot) $对$ \cdot $在分布$ \mathcal{D} $下的数学期望
$ \text{sup}(\cdot) $                  上确界
$ \mathbb{I}(\cdot) $                       指示函数 




### 一、算法的偏好与泛化能力

对于一个算法$ \mathfrak{L}_a $ 若它在某些问题上比算法$ \mathfrak{L}_b$好，则必然存在另一些问题，使得$ \mathfrak{L}_b $比$ \mathfrak{L}_a $好。

对于算法$ \mathfrak{L}_a $, 训练集外的样本误差为：
$$
E_{ote}(\mathfrak{L}_a|X,f)=\sum_h\sum_{x\in (\mathcal{X}-X)}P(x)\mathbb{I}(h(x)\neq f(x))P(h|X,\mathfrak{L}_a)
$$

通过1.4推导可得出，**算法的总误差与学习算法无关，算法的期望性能相同**。

所以局部问题局部求解！！**脱离具体问题谈算法毫无意义**



### 二、K-折交叉验证和自助采样

k次求均值

多次抽取并放回，抽取出来的做训练集，剩余做测试



### 三、 查准率 查全率 F1

混淆矩阵，

查准率P：查出来的有多少是准的

查全率R：对的里面有多少被查出来了

**若一个学习器的PR曲线被另一个学习器的曲线完全包住，则后者性能呢优于前者。一般也可认为平衡点P=R越高者越优**
$$
\frac{1}{F_1} = \frac{1}{2} \cdot (\frac{1}{P}+\frac{1}{R}) \\
F_1 = \frac{2 \times P \times R}{P + R} \\
F_{\beta} = \frac{(1+\beta^2) \times P \times R}{(\beta^2 \times P) + R}
$$
调和平均数比算术平均数，几何平均数**更重视较小值**

### 四、代价矩阵

