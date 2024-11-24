---
tags:
  - math
  - 概率论
  - 统计学
---
### 1. 一个简单的例子

> [!问题1]
> 假设有一列独立同分布的随机变量$X_1,...,X_n \sim \text{Bernoulli}(p)$,给定实数$\alpha,\varepsilon>0$求使得不等式$$P(|p-\overline{X}_n|<\varepsilon)>1-\alpha$$成立的最小的n.(其中$\overline{X}_n = \frac{1}{n}\sum_{n\geq k\geq 1} X_k$)

这个问题就是说我们要得到一个置信水平为$1-\alpha$的区间估计$[\overline{X}_n-\varepsilon,\overline{X}_n+\varepsilon]$所需要的最小样本是多少。

要解决这个问题自然需要对$P(|p-\overline{X}_n|\geq \varepsilon)$做出一个上界的估计得到一个$U_n$，从而我们只需要令$U_n \leq \alpha$，就能解决该问题。而这样的上界估计相当于是要估计,$$P\left(|\mu- \overline{X}_n|\geq \varepsilon \right)\leq ?$$
这个问题当然可以用最基本的Chebyshev不等式(证明可以参考[[有限测度下各个收敛之间的关系]])来完成。由Chebyshev不等式可以得到:

$$P\left(|p- \overline{X}_n|\geq \varepsilon \right)\leq \frac{V(\overline{X}_n)}{\varepsilon^2}=\frac{p(1-p)}{n\varepsilon^2}\leq \frac{1}{4n\varepsilon^2}$$
那么令$\frac{1}{4n\varepsilon^2} \leq \alpha$我们得到$$n\geq \frac{1}{4\alpha\varepsilon^2}$$
那么为何此处还要大费周章去考虑所谓的Hoeffding不等式呢？因为Chebyshev不等式在这个问题上有这样一些缺陷:
1. **不够紧**:Hoeffding不等式给出的上界更紧。之所以可以更紧，是因为要求了独立性，chebyshev只在最后简化方差的部分才会用到独立性。此外Hoeffding不等式还限制了随机变量的上下界。
2. **麻烦**：Chebyshev不等式先会得到一个带有$V(\overline{X}_n)$的结果，然后我们需要使用期望的取值范围之类的条件去对方差做一个上界估计，从而在上界当中去掉参数$\mu$。

> [!Hoeffding不等式]
> 随机变量$X_1,...,X_n$是独立同分布的随机变量并且几乎处处属于区间$[a_i,b_i]$,令$S_n = X_1+...+X_n$那么$$P(S_n-E(S_n)\geq \varepsilon)\leq \exp\left(-\frac{2\varepsilon^2}{\sum_{i=1}^{n} (b_i-a_i)^2}\right)$$以及$$P(|S_n-E(S_n)|\geq \varepsilon)\leq 2\exp\left(-\frac{2\varepsilon^2}{\sum_{i=1}^{n} (b_i-a_i)^2}\right)$$

在问题1的特定情况下，$a_i =0,b_i =1$.因此$$P\left(|p- \overline{X}_n|\right)\leq 2\exp(-2n\varepsilon^2)$$
那么这样我们得到的最小样本的数目的估计就是$$n\geq \frac{\log(2/\alpha)}{2\varepsilon^2}$$
用Mathematica可以得到Hoeffding以及Chebyshev给出的估计的差别。
![[Hoeffding与Chebyshev做对比.png.png]]
此图的代码如下:
```wolfram
Plot[{Log[2/a]*0.5*1000^2, 1000^2/(4*a)}, {a, 0, 0.05}, 
 PlotStyle -> {Red, Blue}, PlotLegends -> {"Hoeffding", "Chebyshev"}, 
 AxesLabel -> {"\[Alpha]"}, PlotLabel -> "epsilon=1/1000下两种方法对n估计"]
```
