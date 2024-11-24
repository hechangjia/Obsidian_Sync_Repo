---
tags:
  - math
  - 数论
---

> [!二项式系数的定义]
> $$\binom{n}{m}=\frac{n!}{m!(n-m)!}$$

> [!问题1]
> 证明$\binom{n}{m}$是整数。

从名字上来说有一个比较显然的途径是证明二项式定理，即$(1+x)^n$
其展开的第m项就是$\binom{n}{m}$.这个过程并不困难，只要对多项式求m此微分，然后令$x=0$便可以得到。

不过我们还可以看看其他更多的有趣途径。

### 1. Legendre公式

这个想法的动机是，既然整数的素因分解是唯一的(整数环作为唯一分解域UFD)，那么$n!$的数因分解是怎样的?也就是说给定一个素数p，那么我想要知道$n!$当中这个素因子的指数$\nu_p(n!)$是多少?

之所以关心这个$\nu_p(n!)$是因为想到既然$\binom{n}{m}$就是由分子一个阶乘，以及分母上两个阶乘构成的，那么只要我们能搞清楚他们的素因分解，那么是否是整数就一目了然了。

不过在语言上，我们可以抽象一点，让这个概念不仅仅限于整数。

> [! padic valuation]
> 考虑这样一个$\nu_p(r)$,其中$r$是非零有理数，假设$r = \frac{a}{b}$.如果把$a,b$都分解为素因子的乘积，那么假设此有理数分子分母当中所包含的所有素因子组成集合$E=\{p_1,...,p_s\}$,那么$r = p_1^{a_1}\cdots p_s^{a_s}$，其中$a_i \in \mathbb{Z}$ (注意有可能会为负数)。那么定义$$\nu_p(r) = \begin{cases}0&p\not \in E\\ a_i&p\in E\land p=p_i\end{cases}$$这是一个$\mathbb{Q}\to \mathbb{Z}\cup \{\infty\}$的函数。

举个例子，$r = \frac{10}{3} = 2\cdot 5 \cdot 3^{-1}$,于是$\nu_2(r)=1,\nu_5(r)=1,\nu_3(r)=-1$其余的素数对应的$\nu_p(r)=0$.

很容易证明给定素数$p$，函数满足性质(表现得像log函数):
1. $\nu_p(r_1r_2)=\nu_p(r_1)\nu_p(r_2)$
2. $\nu_p(r_1/r_2)=\nu_p(r_1)-\nu_p(r_2)$
3. 如果$\nu_p(r)\geq 0$对于任意素数$p$成立，那么$r$一定是整数。相反，如果$\nu_p(r)<0$那么自然这不会是一个整数。
4. $\nu_p(r_1+r_2)\geq \min\{\nu_p(r_1),\nu_p(r_2)\}$如果$\nu_p(r_1)\neq \nu_p(r_2)$那么不等式会取等号。

> [!Legendre 1808]
> n是正整数，对于任意素数p,$$\nu_p(n!)=\sum_{k\geq 1}\left\lfloor\frac{n}{p^k}\right\rfloor$$

那么实际上我们只需要计算，$\nu_p[\binom{n}{m}]$,只要这个结果是非负的，那么二项式系数就是整数。

$$\begin{aligned}\nu_p\left[\binom{n}{m}\right]&= \nu_p\left[\frac{n!}{m!(n-m)!}\right]\\ &= \nu_p(n!)-\nu_p(m!)-\nu_p[(n-m)!] \\ &= \sum_{k\geq 1} \left(\left\lfloor\frac{n}{p^k}\right\rfloor-\left\lfloor\frac{m}{p^k}\right\rfloor-\left\lfloor\frac{n-m}{p^k}\right\rfloor\right) \\ &\geq 0\end{aligned}$$
因为$\nu_p\left[\binom{n}{m}\right]$非负，因此$\binom{n}{m}$是整数。

其中最关键的部分是要说明，对于任意的素数$p$，级数的被求和对象是非负的。实际上这一点是由于

> [!lemma]
> 函数$x,y\in\mathbb{R}$,函数$f(x,y):=\left\lfloor x+y \right\rfloor-\left\lfloor x\right\rfloor-\left\lfloor y\right\rfloor$,此函数非负。

首先注意到，这个函数是一个双周期函数，满足$f(x+1,y)=f(x,y+1)=f(x,y)$,因此函数的值在整个平面上的分布情况实际上是由$\{(x,y):0\leq x,y\leq 1\}$这个正方形区域里面的值决定的。排除掉四个端点的特殊情况以后，实际上我们只需要分为两个区域讨论，$0<x+y<1$,以及$2>x+y>1$，函数的值分别为0以及1。如图所示，一目了然。

```wolfram
Plot3D[Floor[x + y] - Floor[x] - Floor[y], {x, 0, 1}, {y, 0, 1}]
```
![[一个与floor有关的实的算周期函数.png]]

### 2.Kummer定理

#### 2.1 一个具体的问题

考虑这样一个问题，

> [!问题2(伯克利问题6.13.12)]
> 假设$n$是正整数，那么$n$为什么值的情况下，有$$\binom{2n}{n}\equiv0 \text{ mod } 4$$

用上面得语言来阐述这个问题，无非就是问

> [!问题2 版本2]
> 假设$n$是正整数，那么$n$为什么值的情况下$$\nu_2\left[\binom{2n}{n}\right]\geq 2$$

根据问题1的经验，加上对求和(本质上是有限求和，虽然形式上是无穷的)做一些整理，可以得到$$\nu_2\left[\binom{2n}{n}\right]= \sum_{k\geq 1} \left(\left\lfloor\frac{2n}{2^k}\right\rfloor-2\left\lfloor\frac{n}{2^k}\right\rfloor\right)$$
对后者做估计然后得到n需要满足的条件?要做一个这样的精确足够高的估计并不容易。**为什么不把$n$二进制展开呢？**

假设$n = a_0+a_1 2+...+a_s 2^s$,那么此时$$\left\lfloor\frac{n}{2^k}\right\rfloor = \begin{cases}\sum_{i= 0}^{s-k}2^{i} a_{k+i}&k\leq s \\ 0 &k>s\end{cases}$$
那么此时我们可以用n的二进制系数来表达$\nu_2$，假设n的二进制表达当中所有系数的和为$S_2(n)=a_0+...+a_s$那么$$\nu_2\left[\binom{2n}{n}\right]= S_2(n)$$
那么最后的问题就变成了，什么时候$$a_0+...+a_s \geq 2$$
这关系到n的二进制展开有多少位：
1. 如果n是$2^a$的形式，无论a是多少，其二进制表达当中，只有一个系数1，因此上述不等式不能成立。
2. 如果n不是$2^a$的形式，那么其至少有两个不为0的二进制展开系数，那么此时$\nu_2 \geq 2$.
并且我们还可以从以上方法当中知道，一个数二进制展开的非零系数越多，这个数的2-adic valuation才会越大。

#### 2.2 一般情况

模仿上面的过程，考虑$\nu_p\left[\binom{n}{m}\right]$.

> [!Kummer 1852]
> 令$S_p(k)$为正整数k在素数p-adic意义下的展开系数之和，那么$$\nu_p\left[\binom{n}{m}\right] = \frac{S_p(n-m)+S_p(m)-S_p(n)}{p-1}$$

事实上我们只需要在p-adic表示下，重新叙述一下Legendre公式，

> [!Legendre公式 版本2]
> 令正整数$n$的p-adic展开的所有系数和为$S_p(n)$那么$n!$的p-adic valuation可以表示为$$\nu_p(n!)=\frac{n-S_p(n)}{p-1}$$

上面的过程可以用归纳法验证，也可以从经典版本的Legendre公式推导。总之在得到这样的Legendre公式以后，计算$\nu_p\left[\binom{n}{m}\right]$的公式就变得非常容易了。

#### 2.3 一些应用

> [!IMO shortlist 1989]
> 令$f(m)$表示最大的k使得$2^k | m$.求证有无数个整数m满足$$m-f(m)=1989$$

实际上$f(m) = \nu_2(m)$,那么$\nu_2(m) = m -S_2(m) = m-1989$,于是这个式子的解就是所有那些二进制表达当中含有1989个系数1的那些整数，这样的整数显然是无穷多的。

---

> [!美国数学月刊]
> $n,q$是两个正整数，其中$q$的任意素因子都要比$n$更大，求证$$(q-1)(q^2-1)\cdots(q^{n-1}-1)\equiv 0\text{ mod } n!$$

换言之，如果p是n的素因子，那么也就是说在左边素因分解当中$p$的指数至少是$\nu_p(n!)$。

接下来分析左边的素因子p的指数，按照问题的设定，$(p,q)=1$,因此费马小定理告诉我们$q^{p-1} -1 \equiv 0\text{ mod p}$.现在在循环群$\mathbb{Z}_p^{\times}$上考虑这个问题，$\mathbf{q}$是对应的模p以后的剩余类，同时也是群的生成元(费马小定理告诉我们它是p-1阶元)。

我们现在要考虑，$\mathbf{q}^k$里面，还有哪些是单位元，这样我们就知道至少左边有多个素因子p了(只考虑每个$q^k -1$被p整除，忽略被$p^2,p^3,...$整除等情况)。按照循环群的群元素阶的公式$\frac{p-1}{(k,p-1)}=1$,我们知道只有那些不超过$n-1$且是p-1的倍数的那些$k$符合条件，这样的k的个数为
$$\left\lfloor\frac{n-1}{p-1}\right\rfloor$$

这正是我们想要的，因为

> [!对阶乘的p-adic valuation的简单上界估计]
> 对于任意素数p,n!的p-adic valuation有不等式$$\nu_p(n!) \leq \left\lfloor\frac{n-1}{p-1}\right\rfloor$$

原因很简单，$\nu_p(n!)=\frac{n-S_p(n)}{p-1}$，其中n的p-adic展开当中所有系数和至少是1，因此便得到上述不等式。

根据这个不等式，素因子p在n!当中的含量小于等于左边的关于q的式子当中的含量，因此$$(q-1)(q^2-1)\cdots(q^{n-1}-1)\equiv 0\text{ mod } p^{\nu_p(n!)}$$都成立，于是命题成立。



