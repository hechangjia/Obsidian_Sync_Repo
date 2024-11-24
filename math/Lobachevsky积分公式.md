---
tags:
  - math
  - 微积分
---
命题是这样叙述的，对于一个周期为$\pi$的连续的偶函数$f$,有下面的积分不等式:
$$\int_{0}^{\infty} \frac{\sin(x)}{x}f(x)dx = \int_{0}^{\pi/2}f(x)dx$$
### 应用
1. 比如说这样的积分:$$\int_{-\infty}^\infty \frac{\sin(x) (1+\cos(x))}{x(2+\cos(x))} dx$$直接去求是比较困难的，即便是求助Mathematica也不行，但是如果用Lobachevsky的结果，那么就会比较好算$$\int_{0}^{\pi/2} \frac{1+\cos(x)}{2+\cos(x)}dx = \frac{9-2\sqrt{{3}}}{18}$$
2. 同样的比如这个积分:$$\int_{0}^{\infty}\frac{\sin(x)|\sin(x)|}{x}$$这个积分同样使用Lobachevshy公式可以转换为积分$$\int_{0}^{\pi/2}|\sin(x)|dx =1$$
### 傅里展开的做法
1. 带有周期的函数首先很容易想到做Fourier展开。这里我们选择$\{1,\cos(2nx),\sin(2nx)\}$在$[-\pi/2,\pi/2]$上的完备单位正交系。于是$f(x) = \frac{1}{2}a_0+\sum_{n\geq 1}a_n\cos(2nx)+\sum_{n\geq 1}b_n\sin(2nx)$然后由于函数在$[-\pi/2,\pi/2]$上是偶函数，于是$$f(x)=\frac{1}{2}a_0+\sum_{n\geq 1}a_n\cos(2nx)$$然后交换积分和求和的次序,于是得到:$$\begin{aligned}\int_{0}^{\infty} \frac{\sin(x)}{x}f(x)dx &= \sum_{n\geq 1}a_n\int_{0}^{\infty} \frac{\sin(x)}{x}\cos(2nx)dx+\frac{\pi}{4}a_0 \\ &= a_0\frac{\pi}{4} =\frac{\pi}{4}\frac{4}{\pi}\int_{0}^{\pi/2}f(x)dx \\ &= \int_{0}^{\pi/2}f(x)dx\end{aligned}$$
2. 这里面的问题在于，$f$的假设仅仅是连续的，这就有可能会存在它没有傅里叶展开。 
### 把积分按周期分解为求和

其基本的想法是,**在大的范围上的积分分解为一个个周期上积分的和，然后利用对称性制造差**,当然这里产生差是很自然的，因为$\sin(2n\frac{\pi}{2})$以及$\sin((2n-1)\frac{\pi}{2})$的时候会出现符号的相反，于是自然而然地产生了差, $$\begin{aligned}\int_{0}^{\infty} \frac{\sin(x)}{x}f(x)dx &=\sum_{n\geq 0} \int_{n\frac{\pi}{2}}^{(n+1)\frac{\pi}{2}}\frac{\sin(x)}{x}f(x)dx \\&=\sum_{k\geq 0} \int_{0}^{\pi/2} (-1)^k\left(\frac{1}{t+k\pi}+\frac{1}{t-k\pi}\right)f(t)\sin(t)dt \\ &=  \int_{0}^{\pi/2}\sum_{k\geq 0}  (-1)^k\left(\frac{1}{t+k\pi}+\frac{1}{t-k\pi}\right)f(t)\sin(t)dt \\ &= \int_{0}^{\pi/2} f(t)dt \end{aligned}$$
1. 这里面有一个lemma是：对于$\alpha \not \in \pi \mathbb{Z}$
$$\frac{1}{\sin \alpha} = \frac{1}{\alpha} + \sum_{m=1}^{\infty} (-1)^m \left( \frac{1}{\alpha - m\pi} + \frac{1}{\alpha + m\pi} \right) = \sum_{m\in\mathbb{Z}} \frac{(-1)^m}{\alpha + m\pi}
$$一个证明思路是利用函数$f_{\alpha}(x) = e^{i\alpha x}$其在$(-\pi,\pi)$内关于单位正交系$\{e^{inx}\}$的傅里叶展开，因为其傅里叶系数为$$\hat{f}_{\alpha}(n)= \sin(\alpha \pi)\frac{(-1)^n}{\alpha \pi-n\pi}$$
主要的想法是发现，这些傅里叶系数的和恰好可以证明我们需要的恒等式，而**傅里叶系数的和可以理解为函数的傅里叶展开在$x=0$处的取值**。
所以，$$e^{i\alpha x}=\sum_{n\in \mathbb{Z}}\hat{f}_{\alpha}(n)e^{inx}$$那么是不是我们只要令左右两边取极限$x\to 0$，然后右边交换极限和积分(因为是一致收敛的)便得到:
$$\sum_{n\in \mathbb{Z}} \sin(\alpha \pi)\frac{(-1)^n}{\alpha \pi-n\pi} =1$$
2. 以上的证明还可以证明:$$\frac{1}{\sin^2(\alpha)}=\sum_{n\in\mathbb{Z}} \frac{1}{(\alpha+n\pi)^2}$$按照上面的构造，我们意识到实际上是要证明傅里叶系数模的平方和等于1，而傅里叶模的平方和恰好是函数的$L^2$模的平方，这是所谓的Parseval恒等式，于是
$$\begin{aligned}\sum_{n \in \mathbb{Z}} |\hat{f}_{\alpha}(n)|^2&=\sum_{n \in \mathbb{Z}} \sin(\alpha \pi)^2\frac{1}{(\alpha\pi-n\pi)^2} \\ &= \frac{1}{2\pi}\int_{-\pi}^{\pi}|f_{\alpha}(x)|^2dx \\ &= 1\end{aligned}$$这恰好就是我们需要的式子的变形。
