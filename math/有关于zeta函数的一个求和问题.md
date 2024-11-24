---
tags:
  - math
  - 微积分
  - 大学数学竞赛
---

> [!问题]
> 求$$S=\sum_{n\geq 1} \frac{\zeta(2n)}{n(n+1)}$$

### 1.从生成函数的角度思考

基本的想法是得到$\frac{\zeta(2n)}{n}$的生成函数$f(x)$,那么原来的级数就可以转换为一个生成函数的积分问题即$$S=\int_{0}^{1} f(x)\,dx$$
这样做也是有风险的，如果最后的生成函数的积分不容易计算，那么问题还是没有解决。不过这些都要在得到生成函数以后才好下判断。

#### 1.1 求生成函数
* 第一步首先把生成函数当中的$\zeta(2n)$展开为一个新的级数的形式然后交换次序$$\begin{aligned}\sum_{n=1}^{\infty} \frac{\zeta(2n)}{n} x^n &= \sum_{n=1}^{\infty} \frac{1}{n} \sum_{k=1}^{\infty} \left(\frac{\sqrt{x}}{k}\right)^{2n} \\ &= \sum_{k=1}^{\infty}\sum_{n=1}^{\infty} \frac{1}{n}  \left(\frac{\sqrt{x}}{k}\right)^{2n}\end{aligned}$$
* 交换之后发现，其内层级数为一个较为简单的函数的展开，$$\sum_{n=1}^{\infty} \frac{1}{n}  \left(\frac{\sqrt{x}}{k}\right)^{2n}=-\log\left(1-\left(\frac{\sqrt{x}}{k}\right)^{2}\right)$$那么此时的双重级数变成了$$-\sum_{k\geq 1} \log\left(1-\left(\frac{\sqrt{x}}{k}\right)^{2}\right)=-\log\prod_{k \geq 1}\left(1-\frac{(\sqrt{x})^2}{k^2}\right)$$而这个连乘积让我们想起了$\sin(\pi x)$的Hadamard分解(参考[[Wallis公式,正弦函数Hadamard分解互相之间的关系]])，于是$$-\log\prod_{k \geq 1}\left(1-\frac{(\sqrt{x})^2}{k^2}\right) = -\log\left(\frac{\sin(\pi \sqrt{x})}{\pi \sqrt{x}}\right)$$
那么最后生成函数$$f(x)=\sum_{n=1}^{\infty} \frac{\zeta(2n)}{n} x^n= -\log\left(\frac{\sin(\pi \sqrt{x})}{\pi \sqrt{x}}\right)$$

#### 1.2 求积分
这是验证这样做是否有效的最关键一步，如果积分不好算，那么一切都是徒劳。

这里要对生成函数求积分，即$$S=\int_{0}^{1} f(x)\,dx = -\int_{0}^{1} \log\left(\frac{\sin(\pi \sqrt{x})}{\pi \sqrt{x}}\right)\,dx$$
通过一些简单的化简手段，我们意识到此积分的关键不过是要对$\log(\sin(x))x$进行积分而已。因为$$S= -\frac{2}{\pi^2} \int_{0}^{\pi} \log(\sin(t)) t dt + \log(\pi) - \frac{1}{2}
$$
而这个积分并不困难，结果等于$-\pi\log(2)$于是最终$$S = \log(2\pi)-\frac{1}{2}$$

