---
tags:
  - math
  - 调和分析
---

> [!与Jacobi's theta函数有关的函数方程]
> 定义函数：$$\vartheta(t):=\sum_{n\in\mathbb{Z}} e^{-\pi n^2t},t>0$$那么这个函数满足函数方程$$\vartheta(t)=\frac{1}{\sqrt{t}}\vartheta(1/t)$$

* 这个函数与Jacobi的Theta函数$$\Theta(z|\tau):=\sum_{n\in \mathbb{Z}}e^{\pi i n^2\tau}e^{2\pi inz}$$这个函数对全体$\tau\in \mathbb{H},z\in \mathbb{C}$成立，其中$\mathbb{H}$表示复平面的上半平面(不包含实轴)。而上面定义的函数$\vartheta(t)$其实相等于是$$\vartheta(t):=\Theta(0|it)$$
这里要证明是通过联系到[[Possion求和公式]]。

要利用Possion公式我们需要的是对于一个固定的参数$t>0$的函数$g_t(x):=e^{-\pi t x^2 }$的傅里叶变换。因为$\vartheta(t)$可以看成是$\sum_{n\in \mathbb{Z}}g_t(n)$,那么如果利用Possion求和公式得到恒等式，就会是形如$$\sum_{n\in \mathbb{Z}}g_t(n)=\sum_{n\in \mathbb{Z}}\widehat{g_t}(n)$$而关于$g_t(x)$这个函数的傅里叶变换，我们可以从一个已知的结果中得到。假设$f(x):=e^{-\pi x^2}$，这个函数的傅里叶变换非常特殊，因为其傅里叶变换就是自己本身。这两个函数之间具有关系:$$f(\sqrt{t}x)=g_t(x)$$那么我们就可以通过$f$的傅里叶变换推导出$g_t(x)$的傅里叶变换。具体来说$$\widehat{g_t}(\xi)=\frac{1}{\sqrt{t}}\widehat{f}(\xi/\sqrt{t})=\frac{1}{\sqrt{t}}e^{-\pi \xi^2/t}$$于是由Possion公式可得:$$\vartheta(t)=\frac{1}{\sqrt{t}}\vartheta(1/t)$$


