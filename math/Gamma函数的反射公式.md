---
tags:
  - math
  - 复分析
---

> [!反射公式]
> 对于复平面上$z \not \in \mathbb{Z}$的复数$z$都有$$\Gamma(z)\Gamma(1-z)= \frac{\pi}{\sin(\pi z)}$$

对于此公式，我们只需要按照[[为何三角恒等式可以推广到复平面]]当中同样的方法，只需要证明在$x\in (0,1)$当中此性质得到满足，然后可以利用解析延拓把此性质推广到亚纯函数成立的所有地方。

那么这实际上是一个积分恒等式的问题，也就是说

> [!转换后的问题]
> $x \in (0,1)$满足$$\int_{0}^{\infty}t^{x-1}e^{-t}\Gamma(1-x)\,dt= \frac{\pi}{\sin(\pi x)}$$

我们可以尝试[[和以及积分换序]]当中的"积分与积分换序"的想法，因为考虑到$\Gamma(1-x)$本身也是有积分表示的$$\Gamma(1-x)=\int_{0}^{\infty}u^{-x}e^{-u}\,du =t\int_{0}^{\infty}(vt)^{-x}e^{-vt}\,dv$$
后面这一步的$u=vt$的处理是为了等价合并交换做成二重积分的时候方便把而从积分通过换元法转换为一元的积分。

也就是说
$$\begin{aligned}\Gamma(x)\Gamma(1 - x) &= \int_{0}^{\infty} \int_{0}^{\infty} e^{-t(1+v)} v^{-x} \, dv \, dt
\\&= \int_{0}^{\infty} \frac{v^{-x}}{1 + v} \, dv

\\&= \frac{\pi}{\sin \pi(1 - x)}

\\&= \frac{\pi}{\sin \pi x}\end{aligned}$$
交换$v,t$的积分次序以后的积分实际上来自于
$$I = \int_{-\infty}^{\infty} \frac{e^{ax}}{1 + e^x} \, dx = \int_{0}^{\infty} \frac{v^{a-1}}{1 + v} \, dv = \frac{\pi}{\sin \pi a}, \quad a \in (0, 1)
$$
这个结果可以用留数的方法得到。
