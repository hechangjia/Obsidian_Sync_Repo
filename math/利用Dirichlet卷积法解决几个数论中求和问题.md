---
tags:
  - math
  - 解析数论
  - 数论
---

> [!三个类似的求和问题]
> 1. 令$\varphi(k)$为欧拉函数(Euler's totient function)，表示不超过k且与k互素的自然数的个数。求:$$\sum_{k= 1}^{n}\varphi(k)\left \lfloor\frac{n}{k}\right\rfloor$$
> 2. 
> $$\sum_{k= 1}^{n}\mu(k)\left \lfloor\frac{n}{k}\right\rfloor$$其中$\mu$是莫比乌斯(Mobius function)函数
> 3. 
> $$\sum_{k=1}^{n} (-1)^{\Omega(k)} \left \lfloor\frac{n}{k}\right\rfloor$$其中$\Omega(k)$表示k含有多少个不同的素因子。

解决这三个问题的关键想法来自于[[和以及积分换序]]。想法是考虑被求和对象能否展开为新的求和，然后尝试交换次序。


此问题的关键技巧在于，把$\lfloor \frac{n}{k} \rfloor$展开为求和的形式。然后使用双重求和换序的技巧。

为何交换之后就是好算的？因为

1.  在小于 $n$的自然数当中，即集合$\{1,...,n\}$当中能被正整数$k$整除的元素的个数为$\lfloor \frac{n}{k} \rfloor$ 
2.  把这个结果改写为求和的形式，我们利用所谓的指标函数的特性。定义函数$\mathbf{1}_{k|m}= \begin{cases}1 & k|m \\ 0 &\text{otherwise}\end{cases}$,则上述结果可以表达为: $$\left\lfloor
    \frac{n}{k} \right\rfloor = \sum_{m\leq n}\mathbf{1}_{k|m}$$
利用上面的结果，我们可以把原来的三个问题都改写为：
$$\begin{aligned}\sum_{k=1}^{n} f(k)\left\lfloor \frac{n}{k} \right\rfloor
&= \sum_{k\leq n}f(k)\sum_{m\leq n}\mathbf{1}_{k|m}\\ &=
\sum_{m=1}^{n} \sum_{k=1}^{n}f(k)\mathbf{1}_{k|m} \\ &=
\sum_{m=1}^{n} \sum_{k|m} f(k) \end{aligned}$$
第二行我们交换了求和的顺序，第三行因为我们排除了所有不满足$k|m$的求和对象。这样的话最内层的求和便是一个常见的数论函数的Dirichlet卷积，这通常会会导向另一个常见的数论函数。而这些函数的前n项和并不难算。

1. $\sum_{k|m}\varphi(k)=m$ 
2. $\sum_{k|m}\mu(k)=e(m)$,其中$e(m):=\begin{cases}1 & m=1\\0& \text{otherwise}\end{cases}$ 
3. $\sum_{k|m} (-1)^{\Omega(k)} = g(m)$,如果$m$是完全平方数，那么$g(m)=1$否则取0.


所以整个问题结合之前的结论，三个问题的解答分别如下: 

1.  因为$\sum_{k|m}\varphi(k)=m$所以$\sum_{m=1}^{n}\sum_{k|m} f(k) = \sum_{m=1}^{n} m = \frac{m(m+1)}{2}$ 
2.  因为 $\sum_{k|m}\mu(k)=e(m)$ 所以 $\sum_{m=1}^{n}\sum_{k|m} f(k) = \sum_{m=1}^{n} e(m) = 1$ 
3.  因为 $\sum_{k|m} (-1)^{\Omega(k)} = g(m)$ 所以
$$\sum_{m=1}^{n} \sum_{k|m} f(k) = \sum_{m=1}^{n} g(m) =\lfloor \sqrt{n}\rfloor$$
最后第三个问题用到了一个数论的结论，即前n个自然数当中完全平方数的个数为$\lfloor \sqrt{n}\rfloor$.







