---
tags:
  - math
  - 组合学
  - 数论
---

> [!Cauchy Davenport定理(1813,1935)]
> $p$是一个素数，$A,B$是域$\mathbb{Z}/p\mathbb{Z}$的两个子集，证明$$|A+B|\geq \min\{|A|+|B|-1,p\}$$其中$|A+B|$表示两个集合中元素按照域上的加法相加形成的新的集合,$|X|$表示集合的元素的个数。

### 1. 多项式法
#### 1.1 对问题的简化
在开始多项式法的证明之前我们先对问题做一个简化。首先需要指出，CD定理在$|A|+|B|>p$的时候是平凡的。因为

> [!命题1：Cauchy-Davenport的平凡的情形]
> $p$是一个素数，$A,B$是域$\mathbb{Z}/p\mathbb{Z}$的两个子集，如果$|A|+|B|>p$那么$$A+B=\mathbb{Z}_p$$

要证明这个结果，就需要说明对于任意的$z \in \mathbb{Z}_p$存在至少一对$x\in A,y\in B$使得$x+y=z$。不妨换个思路，考虑存在$y=z-x$,也就是说证明$B\cap (z-A)$非空,或者说$|B\cap (z-A)|>0$，这样做的好处就是可以利用起来关于集合尺寸的条件。于是通过$$\begin{aligned}|(z-A)\cap B|&=|(z-A)|+|B|-|(z-A)\cup B|\\&= |A|+|B|-|(z-A)\cup B|\\&\geq|A|+|B|-p>0 \end{aligned}$$
于是得到$$A+B=\mathbb{Z}_p$$
所以接下来的证明中，我们都只考虑$|A|+|B|\leq p$的情形。
#### 1.2 [[组合零点定理]]

> [!证明的基本想法]
> 我们采用反证的办法，我们假设不等式不成立，那么$$|A+B|\leq |A|+|B|-2\leq p-2$$现在我们要让这件事与组合零点定理产生矛盾。我们需要构造一个次数与$|A+B|$有关的，在整个$A\times B$上都为0的，但同时满足组合零点定理的条件的多项式$f(x,y)$。即我们需要多项式$f(x,y)$的次数为$|A|-1+|B|-1$,并且这样次数的单项式系数不为$0_{\mathbb{Z}_p}$。只要这样的多项式存在，那么就会矛盾，而我们期待的好结果是，这样的多项式的存在性是由假设$|A+B|\leq |A|+|B|-2\leq p-2$所保证的。

现在考虑这样一个多项式:$$f(x,y):=\prod_{c\in C}(x+y-c)$$其中$A+B\subseteq C \subset \mathbb{Z}_p$并且$|C|=|A|+|B|-2$。这个多项式满足下面的性质:
1. 此多项式的总次数为$(|A|-1)+(|B|-1)$
2. 其次数为$t_1+t_2$的单项式为$$\binom{|A|+|B|-2}{|A|-1}x^{|A|-1}y^{|B|-1}$$因为组合数中根本不含$p$，因此不可能在$\mathbb{Z}_p$中取到$0_{\mathbb{Z}_p}$。
3. 对任意$a\in A,b\in B$都有$f(a,b)=0_{\mathbb{Z}_p}$
然而这三点却是不符合组合零点定理的，因为前两个条件与第三个条件是矛盾的，因此假设不成立，因此Cauchy-Davenport定理成立。

### 2.调和分析法

#### 2.1 不确定性原理

##### 2.1.1 从Heisenberg不确定性原理

> [!Heisenberg不确定性原理]
> 如果$f \in L^2(\mathbb{R}^n)$的情况下，$$\left(\int_{\mathbb{R}^n}|x|^2|f(x)|^2\,dx\right)\left(\int_{\mathbb{R}^n}|\xi|^2|\widehat{f}(\xi)|^2\,d\xi\right)\geq C_n||f||_{L^2}^4$$其中$C_n$是一个与维度$n$有关的常数。

$V(f):=\int_{\mathbb{R}^n}|x|^2|f(x)|^2\,dx$主要度量函数的"质量或能量"在$\mathbb{R}^n$中相对原点的分布情况。如果这个值相对比较大，说明函数$f$在距离原点较远的区域，或者说函数在交大的空间范围类有显著非零的值。反之，如果$V(f)$比较小，这就意味着函数主要集中在靠近原点的区域内，即他的大部分值都集中在空间的一个相对较小的范围内。总结一下就是$V(f)$大，函数局部化强，$V(f)$小函数局部化弱。

而Heisenberg不确定性原理说的是$$V(f)V(\widehat{f})\geq C_n||f||_{L^2}^4$$也就是说，$f,\widehat{f}$是不能同时局部化的，也就是说二者不能同时都非常集中在$0$附近。

这种现象在有限交换群$G$上也有体现，不过严格的表述形式和$\mathbb{R}^n$上有些许不同。

##### 2.1.2 有限交换群上的不确定性原理

> [!有限交换群上的不确定性原理]
> 假设$G$是一个有限交换群，函数$f:G\to \mathbb{C}$在此群上的傅里叶变换表示为$\widehat{f}:G\to \mathbb{C}$，那么二者的支集的大小满足不等式$$|\text{supp}(f)||\text{supp}(\widehat{f})|\geq |G|$$

* **有限交换群上的傅里叶变换**：参考[[有限交换群上的函数构成的Hilbert空间的结构]]，特别是第二节。

* **证明这种情形下的不确定性原理**:整个证明从对$\widehat{f}$的上确界的控制开始
$$\begin{aligned}\sup_{\xi \in G}|\widehat{f}(\xi)|&\leq \frac{1}{|G|}\sum_{x\in G}|f(x)|\\&= \frac{1}{|G|}\sum_{x\in G}|f(x)|1_{\text{supp}(f)}(x)\\&\leq \mu(\text{supp}(f))^{1/2}||f||_{L^2}\\&=\mu(\text{supp}(f))^{1/2}||\widehat{f}||_{L^2} \\&\leq \mu(\text{supp}(f))^{1/2}\mu(\text{supp}(\widehat{f}))^{1/2}\sup_{\xi \in G}|\widehat{f}(\xi)|\end{aligned}$$这也就导致$$\mu(\text{supp}(f))^{1/2}\mu(\text{supp}(\widehat{f}))^{1/2}\geq 1$$如果$f$并非零函数的话。而$\mu$按照前文的约定是$G$上的单位化后的计数测度，也就是说$$\frac{|\text{supp}(f)|^{1/2}}{|G|^{1/2}}\frac{|\text{supp}(\widehat{f})|^{1/2}}{|G|^{1/2}}\geq 1$$因此不确定性原理中描述的不等式成立。

##### 2.1.3 当群$G$为循环群$\mathbb{Z}/p\mathbb{Z}$时候的改进

如果限定有限交换群$G$为整数模掉一个素数形成的循环群$\mathbb{Z}/p\mathbb{Z}$的时候，2.1.2当中的不确定性原理还能进一步优化。

> [!循环群上的不确定性原理(Tao,2005)]
> 1. 假设$G=\mathbb{Z}/p\mathbb{Z}$其中$p$是素数，函数$f:G\to \mathbb{C}$在此群上的傅里叶变换表示为$\widehat{f}:G\to \mathbb{C}$，那么二者的支集的大小满足不等式$$|\text{supp}(f)|+|\text{supp}(\widehat{f})|\geq p+1$$
> 2. 反过来如果$A,B$是群$G$的两个非空子集，并且其尺寸满足$|A|+|B|\geq p+1$那么一定存在一个函数$f$使得$$\text{supp}(f)=A,\text{supp}(\widehat{f})=B$$

* 这的确是一种优化。因为一般的不确定性原理在此种情况下说的是$$|\text{supp}(f)||\text{supp}(\widehat{f})|\geq p$$而基本不等式告诉我们，按照这个结果，我们能得到的函数及其傅里叶变换的支集尺寸的加法满足的不等式为$$|\text{supp}(f)|+|\text{supp}(\widehat{f})|\geq 2\sqrt{p}$$而tao的这个结果这是把下界给到了$p+1$.
#### 2.2 利用不确定性原理证明Cauchy-Davenport定理

> [!主要思路]
> 1. 第一个想法来自于[[把集合问题转换为函数问题]]当中的基本思路，既然是$A+B$的问题，为何不制造两个函数$f,g$使得二者各自的支集恰好是集合$A,B$于是$$\text{supp}(f*g)\subset \text{supp}(f)+\text{supp}(g)=A+B$$这样一来估计$|A+B|$变成了估计二者卷积的支集。
> 2. 但是凭什么这样的函数存在呢？不确定性原理提供了一个思路，如果存在一个群的子集$X$，能满足$|A|+|X|\geq p+1$那么不确定性原理告诉我们一定存在这样一个$f$使得$$\text{supp}(f)=A,\text{supp}(\widehat{f})=X$$不妨就假设$|X|=p+1-|A|$,同样的事情也能在$B$上发生，假设子集$Y$满足$|Y|= p+1-|B|$那么就一定存在一个$g$使得$$\text{supp}(g)=B,\text{supp}(\widehat{f})=Y$$
> 3. 如此一来就可以对$f*g$这个$\mathbb{Z}/p\mathbb{Z}$上的函数使用不确定性原理中的不等式来估计$|\text{supp}(f*g)|$的大小。

根据以上分析$$\begin{aligned}|A+B|&\geq|\text{supp}(f*g)|\\&\geq p+1-|\text{supp}(\widehat{f*g})|\\&=p+1-|\text{supp}(\widehat{f} \cdot \widehat{g})|\\&= p+1-|\text{supp}(\widehat{f})\cap \text{supp}(\widehat{g})|\\&= p+1-|X\cap Y|\end{aligned}$$所以现在有一个问题选取$X,Y$这两个子集的时候$X\cap Y$究竟取多大比较合适？结合1.1当中命题1提到的Cauchy-Davenport的平凡情形，当$|A|+|B|>p$的时候，此时$|X|+|Y|-p<1$。于是我们不妨取$$|X\cap Y|=\max\{|X|+|Y|-p,1\}$$这样当$|X\cap Y|=1$的时候，也就是一个平凡的情形，按照上面的不等式，此时$|A+B|=p$这个结果与命题1吻合。那么对于不平凡的情况$|X\cap Y|=|X|+|Y|-p$的时候，$$\begin{aligned}|A+B|&\geq 2p+1-(|X|+|Y|)\\&=2p+1-(2p+2-|A|-|B|)\\&= |A|+|B|-1\end{aligned}$$于是综上所述便证明了Cauchy-Davenport定理。