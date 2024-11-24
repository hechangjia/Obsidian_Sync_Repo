---
tags:
  - math
  - 调和分析
  - 实分析
---

> [!上海交大考研数学分析，2014年]
> 假设$f \in C^1([0,\pi]\to \mathbb{R})$，令$$c_n:=\int_{0}^{\pi}f(x)\cos(nx)\,dx$$证明$$\sum_{n\geq 1}|c_n|<+\infty$$

### 1. 证明

这个结果当然让我们会想起[[Riemann - Lebesgue lemma的证明]],以及[[广义的Riemann - Lebesgue lemma]]，此引理直接告诉我们$c_n=o(1)$.但是这显然不够，因为我们需要得到注意判断$c_n$形成的级数是否绝对收敛。那么我们反过来想想，为何该问题的结果会比Riemann-Lebesgue引理更强呢？其实有两点不同：
1. 函数的条件更强：Riemann-Lebesgue引理对函数的要求仅仅是可积，然而这里函数是$C^1$的，这个条件更强。
2. 积分的区间更特殊：[[广义的Riemann - Lebesgue lemma]]当中积分区间$[a,b]$与周期函数并不是适配的，而此处$[0,\pi]$与$\cos(nx)$是适配的。因为我们想到$\{\sqrt{\frac{1}{2\pi}},\sqrt{\frac{1}{\pi}}\cos(nx),\sqrt{\frac{1}{\pi}}\sin(nx)\}_{n\geq 1}$是Hilbert空间$L^2([0,2\pi]\to \mathbb{R})$一单位正交组基。如果我们可以把$f$看成是此空间当中的一个元素，那么我们就可以利用Hilbert空间当中的工具来解决问题了。不过我们这里需要考虑一些定义在$[0,\pi]$上的函数，假设为$g$，定义域稍微与$[0,2\pi]$有一些不同，不过没关系我们可以调整一下，转而考虑$$G(x):=g(x)1_{[0,\pi]}$$如果$g$本身是平方可积的，那么函数$G$显然也是平方可积的，于是$G\in L^2([0,2\pi]\to \mathbb{R})$,那么此时$\int_{0}^{\pi}g(x)\cos(nx)\,dx,\int_{0}^{\pi}g(x)\sin(nx)\,dx$就可以看成是$G$与该空间的单位正交基的其中一部分的内积,也就是$$\int_{0}^{2\pi}G(x)\sqrt{\frac{1}{\pi}}\cos(nx)\,dx=\frac{1}{\pi^{1/2}}\int_{0}^{\pi}g(x)\cos(nx)\,dx$$以及$$\int_{0}^{2\pi}G(x)\sqrt{\frac{1}{\pi}}\sin(nx)\,dx=\frac{1}{\pi^{1/2}}\int_{0}^{\pi}g(x)\sin(nx)\,dx$$

基于以上的特殊性，我们首先想到[[分部积分在积分估计中的用处]]，我们可以利用可微性得到$c_n$的初步估计:$$|c_n|=\frac{1}{n}\left|\int_{0}^{\pi}f'(x)\sin(nx)\,dx\right|=\frac{a_n}{n}$$此时我们还发现$\sum_{n\geq 1}a_n^2$可以保证是收敛的，因为按照上面的分析$f'1_{[0,\pi]}\in L^2([0,2\pi]\to \mathbb{R})$，而$a_n$实际上是$f'1_{[0,\pi]}$在此Hilbert空间的标准正交基下的坐标的其中一部分(正弦的那部分,并且差一个系数)。由于$||f'1_{[0,\pi]}||_{L^2}$是有限的，那么$a_n$的平方和也是有限的(Parseval恒等式)，于是由Bessel不等式得到$\frac{1}{\pi}\sum_{n\geq 1}a_n^2\leq ||f'1_{[0,\pi]}||_{L^2}^2$(详细可以参考[[Hilbert空间当中的基的四个等价命题]])。于是我们想到，与其考虑$c_n$的更为精确的估计从而使用逐项估计，倒不如试试看利用Cauchy不等式进行整体估计。
$$\begin{aligned}\sum_{n\leq N}|c_n|&=\sum_{n\leq N}\frac{|a_n|}{n}\\&\leq \left(\sum_{n\leq N}\frac{1}{n^2}\right)^{1/2}\left(\sum_{n\leq N}a_n^2\right)^{1/2}\\&= O(1)\end{aligned}$$
因此级数$\sum_{n\geq 1}|c_n|$收敛。

### 2. 相关的一个命题

> [!命题1]
> 如果函数$f \in C^{1}(\mathbb{T}\to \mathbb{C})$那么函数的傅里叶级数绝对收敛到函数本身。

实际上也就是证明级数$\sum_{n\in \mathbb{Z}}\widehat{f}(n)$绝对收敛。这个证明几乎是与上面一样的，同样是分部积分，然后利用柯西不等式。

$$\begin{aligned}\sum_{|n|\leq N}\left|\hat{f}(n)\right|&=\left|\hat{f}(0)\right|+\sum_{n \neq 0,|n|\leq N}\left|\hat{f}(n)\right| \\&=\left|\hat{f}(0)\right|+\sum_{n \neq 0,|n|\leq N} \frac{1}{|n|}\left|\hat{f^{\prime}}(n)\right| \\&\leq\left|\hat{f}(0)\right|+\sqrt{\sum_{n \neq 0,|n|\leq N} \frac{1}{n^2}} \sqrt{\sum_{n\neq0,|n|\leq N}\left|\hat{f}^{\prime}(n)\right|^2}\end{aligned}$$而因为$\left\|f^{\prime}\right\|^{2}_{L^2(\mathbb{T})}=\sum_{n \in \mathbb{Z}}\left|\hat{f}^{\prime}(n)\right|^2< +\infty$因此级数是收敛的。

以上两个问题都用到了一个想法:

> [!关键的想法]
> 判断级数$\sum_n a_nb_n$的绝对收敛性的时候，如果发现$\sum_n a_n^2,\sum_n b_n^2<\infty$那么利用柯西不等式可以断定原来级数的收敛。甚至我们可以进一步推广，我们可以尝试用Holder不等式来控制原来的和，即$$\sum_{n\leq N}|a_nb_n|\leq \left(\sum_{n\leq N}|a_n|^p\right)^{1/p}\left(\sum_{n\leq N}|b_n|^q\right)^{1/q}$$此处$1/p+1/q=1,p,q\geq 1$。

比如下面这个例子:

> [!某校数学分析考研题目]
> 假设$\sum_{n\geq 1} a_n$绝对收敛，并且$p>1/2$，证明下面的级数收敛$$\sum_{n\geq 1} \frac{\sqrt{|a_n|}}{n^p}$$

直接利用柯西不等式问题就立刻解决了。