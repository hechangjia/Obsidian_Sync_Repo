---
tags:
  - math
  - tool_idea
---

> [!telescoping sum]
> 但凡我们制造出$f(k+1)-f(k)=g(k)$的形式，我们是有办法直接表示出来$f(k)$的和的。也就是说，我们可以通过函数在整数点处的所有差分的信息还原出函数本身。从这个角度上来说，telescoping sum比较**类似于离散类型的，微积分基本定理**。

### 1.典型的例子

#### 1.1 一个复级数求和

> [!复级数求和]
> $|z|<1$，求和
> $$\sum_{n \geq 1} \frac{z^{n-1}}{(1-z^n)(1-z^{n+1})}$$

* **观察到求和项目可以列开是这个问题的关键**：
$$\frac{z^{n-1}}{(1-z^n)(1-z^{n+1})} = -\frac{1}{(1-z)z} \left(\frac{1}{1-z^{n+1}} - \frac{1}{1-z^{n}}\right)$$
从而可以形成一个telescoping sum,从而立刻知道求和的结果是:
$$-\frac{1}{(1-z)z}\left(1-\frac{1}{1-z}\right) = \frac{1}{(1-z)^2}$$
#### 1.2 关于Fibonacci数的级数

> [!关于Fibonacci数的求和]
> 其中$F_n$是第n个Fibonacci数，$$\sum_{n \geq 1} \frac{1}{F_nF_{n+4}}$$

这个例子告诉我们，有时候发现Telescoping sum也不是那么顺利的，可能会需要多次使用这样的技巧（特别是当分母出现:$f(n)f(n+k)$的时候)

比如这个问题的关键是配出,$$\frac{1}{F_nF_{n+4}} = \frac{1}{3F_{n+2}} \left(\frac{1}{F_n} +\frac{1}{F_{n+4}} \right)$$
这个结果当然不是观察到的，而是设未知数去凑出来的形式。不过这个形式还不能直接发现telescoping sum的形式，而是需要进一步地计算。

我们可以先看一个非常类似但是相对简单的问题，从中找一些经验：
> [!关于Fibonacci数的求和，简单版本]
> 其中$F_n$是第n个Fibonacci数，$$\sum_{n \geq 1} \frac{1}{F_nF_{n+2}}$$


$$\begin{aligned} \sum_{n=1}^{\infty} \frac{1}{F_n F_{n+2}} & =\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{1}{F_n F_{n+2}} \\ & =\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{F_{n+1}}{F_n F_{n+1} F_{n+2}}=\lim _{N \rightarrow \infty} \sum_{n=1}^N \frac{F_{n+2}-F_n}{F_n F_{n+1} F_{n+2}} \\ & =\lim _{N \rightarrow \infty} \sum_{n=1}^N\left(\frac{1}{F_n F_{n+1}}-\frac{1}{F_{n+1} F_{n+2}}\right) \\ & =\lim _{N \rightarrow \infty}\left(\frac{1}{F_1 F_2}-\frac{1}{F_{N+1} F_{N+2}}\right) \\ & =\frac{1}{F_1 F_2}=1 \end{aligned}$$
从解决这个问题的经验中我们知道，首先相差4的可以分拆成两个相差2的，然后相差2的分拆成相差1的，最后一个变成telecscoping sum .于是，这里我们可以把$F_nF_{n+1}$视为一个整体:
$$\begin{align}\sum_{n \geq 1} \frac{1}{F_nF_{n+4}} &= \sum_{n \geq 1} \frac{1}{3F_{n+2}} \left(\frac{1}{F_n} +\frac{1}{F_{n+4}} \right) \\ &= \frac{1}{3} \sum_{n \geq 1} \frac{1}{F_nF_{n+2}} + \frac{1}{3} \sum_{n \geq 1} \frac{1}{F_{n+2}F_{n+4}} \\ &=\frac{1}{3} +\frac{1}{3} \left(\sum_{n \geq 1} \frac{1}{F_{n}F_{n+2}} - \frac{1}{F_1 F_3} - \frac{1}{F_2 F_4}\right) \\&=\frac{1}{3} + \frac{1}{3} \left(\frac{1}{6}\right)\\&=\frac{7}{18}\end{align}$$

### 2.更多的例子

* [[全纯函数沿着两条同伦的连续曲线积分结果一致]]这部分证明当中通过换元发现了telescoping sum的结构，从而完成证明。
