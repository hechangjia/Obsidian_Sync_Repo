---
tags:
  - math
  - 调和分析
---

> [!问题]
> 通过证明下面的积分无界，从而证明Dirichlet kernel,$D_{N}(x)=\frac{\sin\left((N+1/2)x\right)}{\sin(x/2)}$不是[[approximate identity]]. $$\int_{0}^{\pi}\frac{\left|\sin\left((N+\frac{1}{2})t\right)\right|}{t}dt$$ 

自然也无从谈起是好的逼近单位元。

主要是证明这个核并非绝对收敛。
$$\int_{-\pi}^{\pi}|D_N(x)|dx\geq2\int_{0}^{\pi}\frac{\left|\sin\left((N+\frac{1}{2})x\right)\right|}{x}dx$$
所以只要后面的积分是无界的，那么Dirichlet kernel就肯定不是一个逼近单位元。

分子具有周期性，在$[0,\pi]$内的积分会走过很多个周期，于是考虑通过换元得到在$[0,(N+\frac{1}{2})\pi]$上的积分，然分拆积分。最后把不完整的周期分离出去，整个渐进问题就是估计一个不完整的周期，以及在一个周期里面做渐进。于是:$$\begin{aligned}\int_{0}^{\pi}\frac{|\sin((N+1/2)x)|}{x}dx&=\int_{0}^{(N+1/2)\pi}\frac{\sin(t)}{t}dt\\&=\int_{0}^{N\pi}\frac{\sin(t)}{t}dt+\int_{N\pi}^{(N+\frac{1}{2})\pi}\frac{\sin(t)}{t}dt\\&=\sum_{k=0}^{N-1}\int_{k\pi}^{(k+1)\pi}\frac{\sin(t)}{t}dt+O\left(\log\left(1+\frac{1}{2N}\right)\right)\\&=\sum_{k=0}^{N-1}\int_{0}^{\pi}\frac{\sin(s)}{k\pi+s}ds+O\left(\frac{1}{N}\right)\\&=\sum_{k=1}^{N-1}\frac{2}{\pi}\frac{1}{k}+O\left(\frac{1}{N}\right)\\&=\frac{2}{\pi}H_{N-1}+O\left(1\right)\\&=\frac{2}{\pi}\log(N)+O\left(1\right)\\&=\frac{2}{\pi}\log(N)+O(1)\end{aligned}$$
* 中间逐项估计的关键步骤是$\int_{0}^{\pi} \frac{\sin(s)}{k\pi +s}\,ds$这个对象我们对被积分对象的其中一部分做了渐近，而不是对全部做渐近，从而使得做积分以后结果会变得简单。此处$$\int_{0}^{\pi} \frac{\sin(s)}{k\pi +s}\,ds=\frac{2}{\pi k}+O\left(\frac{1}{k^2}\right),k>0$$
