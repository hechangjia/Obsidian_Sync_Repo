---
tags:
  - math
  - 微积分
  - 考研
---

> [!问题(华中科技大学24年考研)]
> 求级数$$\sum_{n=1}^{\infty}(-1)^{n-1}\frac{\log(n)}{n}$$

### 1. 结合Dirichlet的eta函数
因为函数如果不看$\log(n)$的部分的话就是eta函数在$s=1$处的取值，因此尝试把这个级数与eta函数结合起来考虑。

> [!eta函数的定义]
> 对于$\text{Re}(s)>0$,Dirichlet eta函数可以定义为$$\eta(s):=\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^s}$$

此外这个函数与Riemann zeta函数之间有关系$$\eta(s)=(1-2^{1-s})\zeta(s)$$此时我们发现如果我们对$\eta(s)$求微分，那么实际上$$-\eta(s)'=\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^s}\log(n)$$那么实际上问题中需要求的级数就是$-\eta'(1)$,而这个结果我们可以通过zeta函数的一些特殊值来求。因为上述eta函数与zeta函数之间的函数方程的关系，我们还可以把eta函数的微分表示为$$\begin{aligned}\eta'(s)&=2^{1-s}\log(2)\zeta(s)+\zeta(s)'(1-2^{1-s})\\&=\gamma\log(2) -\frac{1}{2}\log^2(2)+O(1-s)\end{aligned}$$
这里我们利用了一些渐近结果:
1. $2^{1-s}=1+\log(2)(1-s)+\frac{1}{2}\log^2(2)(1-s)^2+o(1-s)^2$
2. $\zeta(s)=-\frac{1}{1-s}+\gamma+O(1-s)$
3. $\zeta(s)'=\frac{1}{(1-s)^2}+O(1)$
所以综上所述，$$-\eta'(1)=-\gamma\log(2) +\frac{1}{2}\log^2(2)$$
* 用类似的方式我们也可以证明$$\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n}=\log(2)$$因为这显然就是$\eta(1)$,而与zeta函数的函数方程，以及$s=1$处的渐近展开告诉我们$$\eta(s)=\log(2)+O(1-s)$$所以上面的结果是显然的。
### 2.把交错级数部分和转换为两个部分和之差

> [!基本想法]
> 如果我们要求一个交错级数$\sum_{n=1}^{\infty}(-1)^{n-1}f(n)$。
> 此时我们发现函数具有一部分的“积性”，即虽然不一定$f(2n)$可以直接分开，但是也能转换为已知部分和的情形$g(n)$。那么我们此时有可能通过其部分和求得整个和:$$\begin{aligned}\sum_{n=1}^{2N}(-1)^{n-1}f(n)&=\sum_{n=1}^{2N}f(n)-2\sum_{n=1}^{N}f(2n)\\&= \sum_{n=1}^{2N}f(n)-2\sum_{n=1}^{N}g(n)\end{aligned}$$通常而言，正项级数$\sum_{n=1}^{\infty}f(n)$以及$\sum_{n=1}^{\infty}g(n)$都是发散的级数，不过因为交错级数$\sum_{n=1}^{\infty}(-1)^{n-1}f(n)$是收敛的，假设收敛到$A$，因此此交错级数的部分和应该是$$A+o(1)=\sum_{n=1}^{2N}f(n)-2\sum_{n=1}^{N}g(n)$$因此我们可以分别求两个部分和的渐近展开，然后发散的部分互相抵消以后，就会得到常数项$A$。

在开始解决上文的问题之前我们先来看一个例子:

> [!例子1]
> 假设我们现在要求$\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n}$的一个封闭形式的结果。那么我们发现去掉$(-1)^{n-1}$以后的结果是有一定的积性的，因为$\frac{1}{2n}=\frac{1}{2}\times\frac{1}{n}$。因此我们可以考虑把此级数的部分和表示为两个部分和的差$$\begin{aligned}\sum_{n\leq 2N}\frac{(-1)^{n-1}}{n}&= \sum_{n\leq 2N}\frac{1}{n}-2\sum_{n\leq N}\frac{1}{2n}\\&=H_{2N}-H_N \\ &=(\log(2N)+\gamma+O(N^{-1}))-\log(N)-\gamma+O(N^{-1})\\&= \log(2)+O(N^{-1})\end{aligned}$$因此当$N\to \infty$的时候$$\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n}=\log(2)$$

现在来考虑$\sum_{n=1}^{\infty}(-1)^{n-1}\frac{\log(n)}{n}$。假设$f(n):=\frac{\log(n)}{n}$，这个函数也是具有一定的积性的，因为$$f(2n)=\frac{\log(2)}{2n}+\frac{1}{2}\frac{\log(n)}{n}=\frac{\log(2)}{2n}+\frac{f(n)}{2}$$这个结果前面的部分是调和数，后面的部分就是$\sum f(n)$。于是$$\begin{aligned}\sum_{n\leq 2N}(-1)^{n-1}\frac{\log(n)}{n}&= \sum_{n\leq 2N}\frac{\log(n)}{n}-2\sum_{n\leq N}\frac{\log(2n)}{2n}\\&=\sum_{N< n\leq 2N}\frac{\log(n)}{n}-\log(2)H_N \end{aligned}$$那么很显然我们现在需要对$\sum_{N< n\leq 2N}\frac{\log(n)}{n}$做一个估计，不过还在现在已经去除掉了$(-1)^{n-1}$，因此我们手上的很多工具已经可以使用了。我们的思路是用[[和的积分估计]]这套工具来完成任务。

首先尝试"简单的积分估计"，如果精度不奏效我们再来考虑更为精确但是代价更高的工具。对于上面的问题，我们对精度的要求实际上是很低的，只需要是$o(1)$就够了，而“简单的积分估计”能给到我们至少$O\left(\frac{\log(N)}{N}\right)$的精度,因此其实对于该问题，“简单的积分估计”足以应对。$$\begin{aligned}\sum_{N< n\leq 2N}\frac{\log(n)}{n}&=\int_{N}^{2N}\frac{\log(x)}{x}\,dx + O\left(\frac{\log(N)}{N}\right)\\&=\frac{\log^2(2)}{2} +\log(2)\log(n)+o(1)\end{aligned}$$于是综上所述$$\begin{aligned}\sum_{n\leq 2N}(-1)^{n-1}\frac{\log(n)}{n}&= \sum_{N< n\leq 2N}\frac{\log(n)}{n}-\log(2)H_N \\&= \frac{\log^2(2)}{2} +\log(2)\log(n)+o(1)-\log(2)\left(\log(n)+\gamma+o(1)\right)\\&= \frac{\log^2(2)}{2}-\log(2)\gamma + o(1)\end{aligned}$$因此$N\to \infty$的时候得到和$$\sum_{n=1}^{\infty}(-1)^{n-1}\frac{\log(n)}{n}=\frac{\log^2(2)}{2}-\log(2)\gamma$$
* 不过我们要意识到，这种方法的适用范围并不是很广泛。因为只有很少的$f(n)$拥有上面两个例子当中的性质。比如说如果$f(n)=\frac{\sin(n)}{n}$,那么级数$\sum_{n\geq 1}(-1)^{n-1}\frac{\sin(n)}{n}$这样的级数上面的方法就不适用。