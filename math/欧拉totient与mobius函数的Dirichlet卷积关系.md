---
tags:
  - math
  - 数论
  - 解析数论
---

> [!问题]
> 证明Dirichlet卷积的关系：$$\mu * id = \varphi$$
> 其中$\mu$是mobius函数，$id$是恒等映射($id(x)=x$),$\varphi$是欧拉totient函数。

### 1. 利用积性

第一个想法是利用算数函数的积性，只要算数函数具有积性，那么我们就只需要考虑其在$n=p^k$处的值的情况即可。

$$\displaystyle \mu * id (p^k) = \sum_{d|p^k} \mu(d) id\left(\frac{p^k}{d}\right) = \mu(1)p^k + \mu(p)p^{k-1} = p^{k}(1-\frac{1}{p}) $$

那么实际上我们得到了左边的式子的一个乘积公式，那么我们无非就是要证明欧拉函数等于这个乘积公式

$$\varphi(n)=n \prod_{p|n} (1-\frac{1}{p}) $$
### 2.直接从定义利用求和的技巧

这个思路来自于[[把条件函数展开为新的求和然后换序]]，首先按euler totient函数的求和表示，然后利用交换次序的求和技巧得到此函数的Dirichlet卷积表达。

$$\begin{aligned}\varphi(n)&:=\sum_{(k,n)=1,k\leq n} 1 \\&=\sum_{k\leq n} \sum_{d|(k,n)}\mu(d) \\ &= \sum_{d\leq n} \mu(d)\chi_{d|n}\left(\sum_{k\leq n} \chi_{d|k}\right) \\ &=\sum_{d|n} \frac{n}{d}\mu(d)\\&=  \mu*id(n)\end{aligned}$$

### 3. Mobius inversion

> [!莫比乌斯反演]
> 对于算数函数$f,g$如果满足$f*1=g$那么一定有$$f=g*\mu$$
> 其中$\mu$是Mobius miu函数。

也就是说，只要我们能知道一个函数与1做Dirichlet卷积的结果，那么我们就可以把这个函数表达为某种与莫比乌斯函数有关的卷积。

通过Mobius反演可以立刻得到问题的解答，因为如果我们知道$\varphi * 1 = id$,具体写来就是$\sum_{d|n}\varphi(d)=n$那么根据反演公式$$\varphi=\mu*id$$






