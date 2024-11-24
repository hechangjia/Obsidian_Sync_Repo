---
tags:
  - math
---
> [!Silverman-Toepliz定理,1913]
> $\{a_{nk}\},n\geq k\geq 1$是一个非负的双重序列，并且满足:
> 1. 关于$k$的和为1，即:$$\sum_{k=1}^na_{nk}=1$$
> 2. 当$k$固定的时候，$$\lim_{n\to \infty}a_{nk}=0$$
> 那么对于任意的有极限的序列$x_n$(极限可以是无穷)，都有$$\lim_{n\to \infty}\sum_{k=1}^{n}a_{nk}x_k=\lim_{n\to \infty}x_n$$
* 这里我们完全可以把$\sum_{k=1}^{n}a_{nk}x_k$理解为对$x_k$的前n项和的加权平均值，因为权重系数$a_{nk}$关于k的和为1。典型的比如[[关于一个组合数有关的加权平均的极限问题]]当中$$\frac{\binom{n}{0}x_0+\cdots+\binom{n}{n}x_n}{2^n}$$这个和有一个典型的特点:$\sum_{k=1}^n\frac{\binom{n}{k}}{2^n}=1$，并且对于任意固定的$k$，由于$\binom{n}{k}\leq \frac{n^k}{k!2^n}$因此就可以得到$\frac{\binom{n}{k}}{2^n}\to 0$。
* 另外一个典型的用处是求这样的极限$$\frac{a_1+2a_2+\cdots +na_n}{n^2}$$其中$a_k\to a$。我们可以把结果改造成$\sum_{k=1}^n \frac{k}{n^2}a_k$的样子，但是我们发现$\frac{k}{n^2}$的和并非是$1$,或者一个常数，而是$\frac{n+1}{2n}$。不过既然是接近于常数的结果，我们没有道理不能在误差允许的范围内稍微调整一下结果（思路来自[[利用已知的渐近结果求渐近展开的技巧]]）。比如说假设$S_n=\sum_{k=1}^n \frac{k}{n^2}a_k$,然后$$\begin{aligned}S_n&=\frac{a_1+2a_2+\cdots +(n-1)a_{n-1}}{n^2}+\frac{a_n}{n}\\&\to \frac{a}{2}+0=\frac{a}{2}\end{aligned}$$
### 1. 证明结果
证明的路径是根据分段估计([[分段估计的想法]])，确切的说就是简单的分段估计。理由很简单，因为$x_k$因为是存在极限的，那么在靠近极限的那部分自然是很小的，也就是说整个部分和是呈现一种二分的特点，所以为了精度的我们选择使用分段估计。

假设$x_k$的极限是存在且有限的，不失一般性(并未为了简化问题)，我们可以假设其极限为$0$,令$S_n=\sum_{k=1}^{n}a_{nk}x_k$,那么现在的目的就是要证明$$S_n\to 0$$或者说估计部分和$S_n$。

一个简单的加强命题的做法，使用三角不等式，得到$|S_n|\leq \sum_{k=1}^n|a_{nk}x_k|$,如果$|S_n|$的极限为0，那么$S_n$的极限也为0。

接下来我们开始使用分段估计。此处分段的界限由任意的正实数$\varepsilon$控制，对于这样的固定的$\varepsilon>0$，存在$N_{\varepsilon}$使得任意$k>N_{\varepsilon}$(当然这里也假设$n>N_{\varepsilon}$)都有$|x_k|<\varepsilon$。于是:$$\begin{aligned}|S_n|&\leq \sum_{k=1}^n|a_{nk}x_k|\\ &=\sum_{1\leq k\leq N_{\varepsilon}}|a_{nk}x_k|+\sum_{N_{\varepsilon}<k\leq n}|a_{nk}x_k|\\&< M\sum_{1\leq k\leq N_{\varepsilon}}|a_{nk}|+\varepsilon  \end{aligned}$$
* 对于极限为$0$的序列$|x_k|$而言，它一定是有界的，此处$M$为其上界。
因为对于任意固定的$k$,条件告诉我们$a_{nk}\xrightarrow{n\to \infty}0$,于是我们可以两边对$n$取上极限，于是得到:$$\limsup_{n\to \infty}|S_n|\leq \varepsilon$$因为这个结果对任意$\varepsilon>0$成立，因此$|S_n|$的极限存在且为0，这意味着$S_n\to 0$。
