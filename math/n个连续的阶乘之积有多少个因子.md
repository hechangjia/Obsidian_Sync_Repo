---
tags:
  - math
  - 解析数论
---

> [!问题1]
> 函数$d(n)$表示整数$n$的因子的个数，定义$$D(n):=d(1!\cdot 2!\cdots n!)$$求极限$$\lim_{n\to \infty}D(n)^{1/n}$$

### 1. 分析一下大整数

> [!初步想法]
> 数论函数$d(x)$是具有不完全积性的函数，即如果有两个互素的整数$(m,n)=1$，那么$d(mn)=d(m)d(n)$。那么既然我们需要分析的大数有很明显的乘法结构，我们可以分析一下其素因分解，从而简化$d$这个函数的表达，方便做进一步的渐近分析。

我们不难发现$1!\cdot2!\cdots n!$的素因子其实是很小的，相对于这个大数而言。因为其素因子必须满足$p\leq n$,于是$$1!\cdot2!\cdots n!=\prod_{p\leq n}p^{E_p(n)}$$其中$E_p(n)$是这个大整数的素数$p$因子的指数。而要知道这一点，实际上我们只需要知道对于每个阶乘$k!$当中素数$p$的指数$e_p(k!)$，因为$$E_p(n)=\sum_{k=1}^{n}e_p(k!)$$而$e_p(k!)$的结果是一个经典的结果，参考[[从二项式系数到Kummer定理]]当中第一节的Legendre公式，于是:$$E_p(n)=\sum_{k=1}^{n}\sum_{j\geq 1}\left\lfloor \frac{k}{p^j}\right\rfloor$$
### 2. 做渐近分析

我们最终的目标是分析$D(n)^{1/n}$。换一个更易于处理的形式，也就是分析$\frac{1}{n}\log(D(n))$，精度的要求是$o(1)$,这样的话倘若我们得到$\frac{1}{n}\log(D(n))=A+o(1)$,那么我们最终的渐近结果就是$D(n)^{1/n}\to e^{A}$.

因此我们实际上就是需要：

> [!问题2]
> 对$\log(D(n))$做渐近，精度要求是$o(n)$。

根据上面的分析$$\begin{aligned}\log(D(n))&=\log\left(d\left(\prod_{p\leq n}p^{E_p(n)}\right)\right)\\&= \log\left(\prod_{p\leq n}\left(E_p(n)+1\right)\right)\\&= \sum_{p\leq n}\log(E_p(n)+1)\end{aligned}$$
因此我们需要对$E_p(n)$做一个渐近分析。这里我们用非常粗糙的估计，即$\lfloor x\rfloor=x+O(1)$,并且注意到$p^j>n$那么取整函数实际上就是0，于是:
$$\begin{aligned}E_p(n)&=\sum_{k=1}^{n}\sum_{j\geq 1}\left\lfloor \frac{k}{p^j}\right\rfloor\\&= \sum_{j\geq 1}\sum_{k=1}^{n}\left\lfloor \frac{k}{p^j}\right\rfloor \\&= \sum_{j\geq 1}\sum_{k=1}^{n}\left\lfloor \frac{k}{p^j}\right\rfloor \\&=\left(\sum_{p^{j}\le n}\frac{n^2}{2p^j}\right)+O(n)\\&= \frac{n^2}{2(p-1)}+O(n)\end{aligned}$$

现在对于$\log(D(n))$我们不妨进行[[逐项估计]]，也就是估计和中的每一项$\log(E_p(n)+1)$,我们得到$$\begin{aligned}\log(E_p(n)+1)&=\log\left(\frac{n^2}{2(p-1)}+O(n)\right)\\&= \log\left(\frac{n^2}{2(p-1)}\right)+O(1)\\&= 2\log(n)-\log(p-1)+O(1)\end{aligned}$$接下来我们需要把逐项估计的结果放到和式当中去，这里面我们自然要考虑不超过$n$的素数大致有多少个的问题，当然这是非常著名的结果：

> [!素数定理,Poussin&Hadamard 1896]
> $\pi(x)$为素数计数函数，此函数定义为不超过$x$的素数的个数，即$$\pi(x):=\#\{p\in \mathbb{P}:p\leq x\}$$那么关于此函数我们有渐近展开$$\pi(x)=\frac{x}{\log(x)}+O\left(\frac{x}{\log(x)\log(x)}\right)$$

$$\begin{aligned}\log(D(n))&= \sum_{p\leq n}\log(E_p(n)+1)\\&= \sum_{p\leq n}\left(2\log(n)-\log(p-1)+O(1)\right)\\&= 2n-\sum_{p\leq n}\log(p-1)+O\left(\frac{n}{\log(n)}\right) \end{aligned}$$

所以最后问题的关键在于:

> [!问题3]
> 给出$\sum_{p\leq n}\log(p-1)$的精度在$o(n)$的渐近展开结果。

令$f(x):=\sum_{p\leq x}\log(p-1)$，那么这个函数很难不让我们想到Chebyshev函数，其渐近结果算是素数定理的一个中间结果。

> [!引理1:Chebyshev的theta函数的一个粗糙的渐近]
> $\theta(x):=\sum_{p\leq x}\log(p)$,那么$$\theta(x)=x+o(x)$$

而我们要估计的$f(x)$形式上是非常类似于$\theta(x)$的，那么很自然的，我们借助于[[利用已知的渐近结果求渐近展开的技巧]]，我们想到如果$f(x)-\theta(x)=o(x)$,那么我们的目标也就完成了。

于是我们现在的目标就变成了:

> [!问题4]
> 估计$f(x)-\theta(x)$的精度要求为$o(x)$。

$$\begin{aligned}f(x)-\theta(x)&=\sum_{p\leq x}\log(p-1)-\log(p)\\&=\sum_{p\leq x}\log(1-1/p)\\&= -\sum_{p\leq x}\frac{1}{p}+O\left(\sum_{p\leq x}\frac{1}{p^2}\right)\\&= -\log\log(x)+O(1)\end{aligned}$$

最后一步我们使用了[[素数倒数和的估计]]当中的Mertens估计的结果。总之最后的结果表明我们一开始的猜测是对的，我们可以得到$$f(x)=\theta(x)+o(x)=x+o(x)$$于是现在我们回到问题3,$$f(n)=\sum_{p\leq n}\log(p-1)=n+o(n)$$于是现在我们来回答问题2：
$$\begin{aligned}\log(D(n))&= 2n-\sum_{p\leq n}\log(p-1)+O\left(\frac{n}{\log(n)}\right) \\&= 2n-n+o(n)\\&= n+o(n)\end{aligned}$$于是我们知道$$\frac{1}{n}\log(D(n))=1+o(1)$$因此最终我们可以回答问题1的答案，$$D(n)\to e$$
