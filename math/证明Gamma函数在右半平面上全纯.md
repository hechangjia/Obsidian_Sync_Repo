---
tags:
  - math
  - 复分析
---

> [!问题·]
> Gamma函数的积分表示可以在半平面$\text{Re}(s) >0$内定义一个全纯函数.
> $$\Gamma(s):=
> \int_{0}^{+\infty}t^{s-1}e^{-t}dt$$


其本质是考虑到Gamma函数是由$f(s,t):= t^{s-1}e^{-t}$一个定义在$\Omega \times[a,b]$上的函数关于参数的积分表示的，其中$\Omega$表示右半平面$[a,b] \subset (0,+\infty)$。被积函数是一个连续函数，同时固定$t$以后又是$\Omega$上的全纯函数，那么考虑到[[证明某种积分表示的函数是整函数]]当中的命题"**由积分给出的函数是否全纯的充分条件**"，那么很自然地想到用先证$$\Gamma_{\varepsilon}(s):=

\int_{\varepsilon}^{1/\varepsilon}t^{s-1}e^{-t}dt$$对于任意$\varepsilon >0$的时候这个函数是在$\Omega$上全纯的，然后只要$\Gamma_{\varepsilon}(s)$一致收敛到$\Gamma(s)$问题就能解决.

这也是非常常见的[[an epsilon of room]]的做法，即如果我有一个关于函数$\Gamma(s)$的问题，这个问题不好直接处理，然后我们想到可以先做一个$\Gamma_{\varepsilon}(s)$的问题，然后想办法把关于$\Gamma_{\varepsilon}(s)$的性质过渡到原来的函数上，通常需要某种情况下的收敛的性质。

1.  估计误差:$$\begin{aligned}|\Gamma(s)-\Gamma_{\varepsilon}(s)|
    &\leq \int_{0}^{\varepsilon} t^{\sigma-1}e^{-t}dt +
    \int_{1/\varepsilon}^{\infty}t^{\sigma-1}e^{-t}dt \\
    &\leq \frac{\varepsilon^{\sigma}}{\sigma} +
    \int_{1/\varepsilon}^{\infty} t^{\sigma-1}t^{-\sigma-1 } dt
    = \frac{\varepsilon^{\sigma}}{\sigma}+\varepsilon
    \end{aligned}$$这个过程中我们意识到，估计的过程中应该让$\sigma =\text{Re}(s)$在一个有限的范围内，否则上面的讨论会很麻烦。于是上面的式子可以保证对于任意的一个带状区域$\sigma \in (c,d),a>0$上，$\Gamma_{\varepsilon}(s)$一致收敛到$\Gamma(s)$。
2.  于是我们可以知道在任意的$\Omega$内的任意一个带状区域上，$\Gamma(s)$是全纯的。由于我们可以把整个$\Omega$表示为这些带状区域的并，因此$\Gamma(s)$在整个$\Omega$上全纯。
