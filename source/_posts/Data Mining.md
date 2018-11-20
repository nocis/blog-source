---
title: What is data?
date: 2018-03-06 11:45:41
tags: data mining
mathjax: true
categories: data mining
---

## Data Object And Attribute

**attribute :** dimension, feature, variable

**nominal attribute :** hair_color 、 marital_status

**binary attribute :** bool

**ordinal attribute :** ranking

**numeric attribute :**


## Statistical Description

**measure of central tendency :** mean, median, mode, midrange

**measure of Data dissemination :** range, quantile, IQR, boxplot, variance, standard deviation

## Data Matrix And Dissimilarity Matrix

**data matrix :** 
$$
\left[
\begin{matrix}
x_{11}&\cdots&x_{1f}&\cdots&x_{1p}\\
\cdots&\cdots&\cdots&\cdots&\cdots\\
x_{i1}&\cdots&x_{if}&\cdots&x_{ip}\\
\cdots&\cdots&\cdots&\cdots&\cdots\\
x_{p1}&\cdots&x_{pf}&\cdots&x_{pp}\\
\end{matrix}
\right]\\
(n\ objs\ \times p\ attributes)
$$

**Dissimilarity Matrix :** 
$$
\left[
\begin{matrix}
0\\
d(2,1)&0\\
d(3,1)&d(3,2)&0\\
\vdots&\vdots&\vdots\\
d(n,1)&d(n,2)&\cdots&\cdots&0\\
\end{matrix}
\right]\\
(n\ objs\ \times n\ objs)
$$

1. **nominal attribute **

    **mismatch rate :** $d(i,j) = \frac{p - m}{p}$

    p:Total attribute

    m:match attribute


2. **binary attribute **

    **mismatch rate :** $d(i,j) = \frac{r + s}{q + r + s + t}$

    q:the num of both i's and j's attribute whose value equals 1

    t:the num of both i's and j's attribute whose value equals 0

    s:the num of attributes whose value equals 0 for i and 1 for j

    r:the num of attributes whose value equals 1 for i and 0 for j

    ignore t: $d(i,j) = \frac{r + s}{q + r + s}$

    **Jaccard coefficient :** $d(i,j) = \frac{q}{q + r + s}$

3. **numeric attribute **

    **Euclid  distance (2-norm):** $d(i,j) = \sqrt{(x_{i1}-x_{j1})^{2}+(x_{i2}-x_{j2})^{2}+\cdots+(x_{ip}-x_{jp})^{2}}$

    **Manhattan  distance (1-norm):** $d(i,j) = |x_{i1}-x_{j1}|+|x_{i2}-x_{j2}|+\cdots+|x_{ip}-x_{jp}|$

    Euclid and Manhattan's nature:

    1. Non-negative $d(i,j) \ge 0$
    2. $d(i,i) = 0$
    3. Symmetry $d(i,j) = d(j,i)$
    4. $d(i,j) \le d(i,k) + d(k,j)$

    **Minkowski  distance (p-norm):** $d(i,j) = \sqrt[h]{|x_{i1}-x_{j1}|^{h}+|x_{i2}-x_{j2}|^{h}+\cdots+|x_{ip}-x_{jp}|^{h}}$

    **Chebyshev  distance ($\infty$-norm):** the maximum of each attribute's distance $$d(i,j) = \lim_{h \to 0} \left( \sum_{f=1}^p |x_{if}-x_{jf}|^{h}\right)^{\frac{1}{h}} = \max_{f}^{p}|x_{if}-x_{jf}|$$

4. **ordinal attribute **

    mapping [0.0, 1.0]


5. **mixed type**

    weighted mean

6. ** cosine similarity**

    $$
    sim(x,y) = \frac{x \cdot y}{||x||\ ||y||}\\
    Tanimoto\ Distance: sim(x,y) = \frac{x \cdot y}{x \cdot x + y \cdot y - x \cdot y}\\
    ||x||:Euclid\  distance
    $$





