---
tags:
  - math
  - tool_idea
---
这个方法是来自于[[把条件函数展开为新的求和然后换序]]，此方法主要解决的问题是形如这样的求和$$S=\sum_{n\geq 0} a_n \mathbf{1}_{k|n}(n)$$
其中$$\mathbf{1}_{k|n}(n):=\begin{cases}1&k|n \\ 0&\text{otherwise}\end{cases}$$
求和当中，我们假定$a_n$的生成函数$g(x)=\sum_{n\geq 0}a_n x^n$是已知的并且可以表达成简单的函数。于是这里的roots of unity filter不过是一种把$\chi_{k|n}$展开为一个有限的求和的办法而已，具体展开为$$\mathbf{1}_{k|n}(n) =\frac{1}{k}\sum_{m=0}^{k-1}\xi^{m n}$$其中$\xi = e^{\frac{2\pi i }{k}}$.

那么接下来$$\begin{aligned}S &=\sum_{n\geq 0} a_n \mathbf{1}_{k|n}(n) \\&= \sum_{n\geq 0} a_n \frac{1}{k}\sum_{m=0}^{k-1}\xi^{m n} \\ &= \frac{1}{k}\sum_{m=0}^{k-1}\sum_{n\geq 0}a_n \xi^{m n}\\&= \frac{1}{k}\sum_{m=0}^{k-1}g(\xi^m)\end{aligned}$$
因为按照我们之前的假设，生成函数$g$是简单而且好算的，而外层的求和不过是一个有限求和，那么问题也就被解决了。

### 1. 展开的根据是什么

此技巧的来源是把一个定义在群上的函数进行傅里叶展开。

我们可以把此判断函数视为，判断$n$模k之后是否为0的判断，也就是说视为$\mathbb{Z}/k\mathbb{Z}$这个模k的加法群上的一个判断函数。这种等价性来自于函数的取值只能是$0,1$.假设有这样一个判断函数$f(\mathbf{n})$定义在$\mathbb{Z}/k\mathbb{Z}$上，其中$\mathbf{n} \in \mathbb{Z}/k\mathbb{Z}$为是自然数$n$模$k$的剩余类。$$f(\mathbf{n}):=\begin{cases}1&\mathbf{n}=\mathbf{0}\\ 0&\text{ otherwise}\end{cases}$$那么我们可以断言$$\mathbf{1}_{k|n}(n) = f(\mathbf{n})$$
也就是说我们只需要在$\mathbb{Z}/k\mathbb{Z}$上展开函数$f$就行了。按照有限Abel群上傅里叶展开，我们要确认此群的对偶群。实际上此群的对偶群，恰好就是k次单位根因为乘法形成的群$\mathbb{Z}(k):=\{\xi^0,...,\xi^{k-1}\}$其中$\xi = e^{\frac{2\pi i }{k}}$。于是$$f
= \sum_{e \in \mathbb{Z}(k)} \widehat{f}(e) e$$
其中傅里叶系数$$\begin{aligned}\widehat{f}(e) &= \frac{1}{k}\sum_{a \in \mathbb{Z}/k\mathbb{Z}} f(a)\overline{e(a)} \\ &= \frac{1}{k}f(\mathbf{0})\overline{e(\mathbf{0})} = \frac{1}{k}\end{aligned}$$
那么$$f(\mathbf{n})=\frac{1}{k}\sum_{m=0}^{k-1}\xi^{m \mathbf{n}}=\frac{1}{k}\sum_{m=0}^{k-1}\xi^{m n}$$

最后我们便得到了$\mathbf{1}_{k|n}(n)$的展开。


