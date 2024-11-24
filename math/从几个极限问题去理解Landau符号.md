---
tags:
  - math
  - 微积分
---
### 1. 问题1 

> [!问题1]
> 令$$S_n:=\sum_{k\leq n}\sin(k/n^2)$$求$$\lim_{n\to \infty }S_n$$

这里$S_n$是一个关于$n$的比较复杂的序列，而我们想要给它一个“渐近分析”，再具体一点通过渐近分析求得其极限。说白了就是得到$$S_n = A+o(1)$$即写成一个常数加上一个无穷小。这里有一个Landau符号"$o(1)$"这是什么意思?

> [!关于o(1)]
> $o(f(n))$表示得是一个序列的对象，我们可以记作$a_n$。它的含义是：“当n足够大的时候$|a_n|\leq \varepsilon f(n)$”，或者严格一点，对任意的$\varepsilon>0$存在正整数$N_{\varepsilon}$使得所有$n>N_{\varepsilon}$都有$$|a_n|\leq \varepsilon f(n)$$我们可以理解为,虽然这个对象$a_n$的细节可能非常复杂，但是我知道，它在n很大的时候其增长速度远远小于一个简单的对象$f(n)$。当然我知道有的朋友喜欢用$|a_n|/f(n)\to 0$来理解，不过相对而言其实用不等式的方式理解更为方便灵活。

那么现在我们来看$S_n$的渐近展开的方法。其实本质上就是[[逐项估计]]。

> [!主要想法]
> 如果我们使用Taylor展开每一项，然后对每一项做估计，然后估计误差的累积可能就会达到我们的目的,只要误差的累积可以被$o(1)$控制起来。

我们发现$\sin(k/n^2)=\frac{k}{n^2}+o(\frac{k}{n^2})$,那么$$\begin{aligned}S_n&=\frac{n(n+1)}{2n^2}+o\left(\frac{n(n+1)}{2n^2}\right)\\&= \frac{1}{2}+o(1)+o(1)\\&= \frac{1}{2}+o(1)\end{aligned}$$
第一行的求和的意思:
1. 首先我们利用的是$$\sin(x)=x+o(x)$$对任意$\varepsilon>0$,存在$\delta_{\varepsilon}>0$使得对任意$|x|<\delta_{\varepsilon}$都有$R(x):=\sin(x)-x$满足不等式$$|R(x)|\leq \varepsilon x$$这意味着假设我们有$m$个值$x_1,....,x_n$都满足$|x_i|<\delta_{\varepsilon}$,那么我们完全可以把这些结果加起来使得$$\sum_{k\leq n}\sin(x_k)=\sum_{k\leq n}x_k+\sum_{k\leq n}R(x_k)$$而我们知道每个$R(x_k)$都满足不等式，于是$$\sum_{k\leq n}R(x_k)\leq \varepsilon\sum_{k\le n}x_k$$于是我们可以写作$$\sum_{k\leq n}\sin(x_k)=\sum_{k\leq n}x_k+o\left(\sum_{k\leq n}x_k\right)$$
2. 现在的情况是我们知道，任意的$f(n,k):=\frac{k}{n^2}\leq \frac{1}{n}$,当n足够大的时候是可以任意小的。因此我们知道，对任意的$\delta_{\varepsilon}>0$存在正整数$N_{\varepsilon}$使得$n>N_{\varepsilon}$的时候$|f(x,k)|<\delta_{\varepsilon}$，于是参照上面的分析得到$$\sum_{k\leq n}\sin(k/n^2)=\frac{n(n+1)}{2n^2}+o\left(\frac{n(n+1)}{2n^2}\right)$$
第二行的意思是：
1. 我们知道$\frac{n(n+1)}{2n^2}=\frac{1}{2}+\frac{1}{2n}$,其中$1/2n$这个对象满足不等式，对任意的$\varepsilon>0$，当n足够大的时候有不等式$1/2n \leq \varepsilon$，所以我们表示为$\frac{1}{2n}=o(1)$。
2. 按照同样的道理，那么第二部分$o(\frac{1}{2}+\frac{1}{2n})$是什么意思？同样的，表示一个对象，假设为$b_n$好了，满足对任意的$\varepsilon>0$,n足够大的时候$|b_n|\leq \varepsilon(\frac{1}{2}+\frac{1}{2n})\leq \varepsilon$所以很自然地我们也把它表示为$o(1)$
3. 最后一行我们用到了一个关于o的运算律，$o(1)+o(1)=o(1)$，这是什么意思呢?假设等式左边两个o代表的对象是$a_n,b_n$，对任意的$\varepsilon/2>0$,都存在$N'_{\varepsilon},N''_{\varepsilon}$使得$n>\max\{N'_{\varepsilon},N''_{\varepsilon}\}$的时候，$$|a_n|\leq \frac{\varepsilon}{2},|b_n|\leq \frac{\varepsilon}{2}\implies |a_n+b_n|\leq \varepsilon$$所以我们也可以用$o(1)$表示整个$a_n+b_n$。因此$o(1)+o(1)=o(1)$
那么现在即便是得到了$S_n = \frac{1}{2}+o(1)$又如何?其实我们得到的是一个不等式，什么不等式?对任意的$\varepsilon>0$存在正整数$N_{\varepsilon}$，使得任意的$n>N_{\varepsilon}$都有$$|S_n-\frac{1}{2}|\leq \varepsilon$$这意味着$S_n\to \frac{1}{2}$。

所以诸位网友请看，全程我们是不涉及极限符号使用的，但是处处都是谈论极限，并且Landau符号的使用是严格的。

### 2. 问题2

> [!问题2]
> 令$$A_N:=\prod_{n\leq N}\frac{n}{n+a}$$其中$a$是一个固定的实数，求$$\lim_{n\to \infty }A_N$$

> [!主要想法]
> 把乘积通过指数映射转换为和，然后对和做渐近分析。

令$S_N:=\sum_{n\leq N}\log(n)-\log(n+a)$,于是$$\begin{aligned}S_N&=\sum_{n\leq N}\log(n)-\log(n+a) \\&= -\sum_{n\leq N}\log\left(1+\frac{a}{n}\right)\\&= -\left(\sum_{n\leq N} \frac{a}{n}\right)+O\left(1\right)\\&= -aH_{N}+O(1)\end{aligned}$$
1. 第二步，借助于函数$\log(1+x)=x+O(x^2)$这样的Taylor展开,其含义是$\forall \varepsilon>0$存在$\delta_{\varepsilon}>0$使得所有满足$|x|<\delta_{\varepsilon}$都有$|\log(1+x)-x|<\varepsilon x^2$，而无论$a$是什么实数，只要是固定不变的，那么由于$\frac{a}{n}\to 0$,那么就存在足够大的$N_{\varepsilon}$使得当$n>N_{\varepsilon}$的时候可以令$x=\frac{a}{n}$带入到$\log(1+x)$的渐近展开中。至于说$n\leq N_{\varepsilon}$的部分，因为这部分是有限的，于是我们用一个$O(1)$控制起来。
2. 第三行，这里其实省略了，$O\left(\sum_{N\geq n>N_{\varepsilon}}\frac{a^2}{n^2}\right)+O(1)=O(1)$因为$\frac{1}{n^2}$形成的级数是收敛的，因此整个和可以被一个常数控制起来，此外再加上一个被常数控制的项，最终依旧可以被常数控制。
3. 最后的$H_N:=\sum_{n\leq N}\frac{1}{n}$是调和级数的前N项和，这是单调增加且无界的一个序列。因此如果$a> 0$,那么$S_N\to -\infty$。此外$A_N=\exp(S_N)$,于是$A_N$的极限为0。