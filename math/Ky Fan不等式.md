---
tags:
  - math
  - 调和分析
---

> [!Ky Fan不等式]
> 假设有$n$个实数分别是,$x_0,...,x_{n-1}$并且满足$$\sum_{k=0}^{n-1}x_k=0$$于是成立不等式$$\sum_{k=0}^{n-1}x_kx_{k+1}\leq \cos\left(\frac{2\pi}{n}\right)\sum_{k=0}^{n-1}x_k^2$$
> 其中约定$x_0=x_{n}$。

### 1.调和分析的做法

#### 1.1 问题的翻译

最后的约定，$x_0=x_n$倒是提醒我们可以把序列看成是在群$G=\mathbb{Z}/n\mathbb{Z}$上的函数，于是我们可以把问题翻译为:

> [!Ky Fan不等式的函数版本]
> 考虑群$G=\mathbb{Z}/n\mathbb{Z}$以及此群上建立的Hilbert空间$L^2(\mu,G\to\mathbb{C})$,其中$\mu$是单位化了的计数测度。令$f \in L^2(\mu,G\to\mathbb{C})$的一个***实值函数***，满足条件$$\int_{x\in G}f(x)\,d\mu(x)=0$$如果用$Tf(x):=f(x+1_G)$表示令函数$f$在群$G$上平移一个单位,那么在函数$f$一定满足不等式$$\langle f,Tf \rangle\leq \cos\left(\frac{2\pi}{n}\right)||f||_{L^2}^2$$

首先我们来大致分析一下这个命题与原版的Ky Fan不等式之间的等价性，基本内容可以参考[[有限交换群上的函数构成的Hilbert空间的结构]]
1. 为什么在群$G$上?因为$x_0=x_n$实际上表明这里面存在循环的结构，所以考虑循环群是自然的。
2. 一开始的条件$\int_{x\in G}f(x)\,d\mu(x)=0$实际上也就是一个求和的形式$$\frac{1}{n}\sum_{x \in G}f(x)=0$$因此==本文使用带单位计数测度的积分符号替代求和符号，纯粹是为了体现群$G$上的傅里叶分析与经典的常见的其他傅里叶分析的相似之处，实际上表达的含义是等价的。==
3. 内积与模：$$\langle f,g\rangle:=\int_{G}f(x)\overline{g(x)}\,d\mu(x)=\langle f,g\rangle:=\frac{1}{|n|}\sum_{x\in G}f(x)\overline{g(x)}$$而$L^2$模的平方也就是$\langle f,f\rangle$。而函数是实值函数，因此内积当中的共轭操作可以忽略。

#### 1.2问题的初步分析

1. 如果忽略一开始的$\int_{x\in G}f(x)\,d\mu(x)=0$的条件，我们能得到一个关于控制内积$\langle f,Tf \rangle$的很粗略的结果，因为$$|\langle f,Tf \rangle|\leq ||f||_{L^2}||Tf||_{L^2}$$而平移式是不会改变函数的模的，因为$$\sum_{x \in G}f^2(x)=\sum_{x \in G}f^2(x+1_G)$$(或者也可以说计数测度是Haar测度，保持在群上的平移不变性)总之$||Tf||_{L^2}=||f||_{L^2}$，于是得到$$|\langle f,Tf \rangle|\leq ||f||_{L^2}^2$$不过和Ky Fan不等式想比，上界的系数差距还是比较大的，特别是n比较大的时候。我们会意识到，会有这样的差距，可能是条件$\int_{x\in G}f(x)\,d\mu(x)=0$造成的。
2. 条件$\int_{x\in G}f(x)\,d\mu(x)=0$不禁让我们想起，在群$\mathbb{T}$上证明过的[[Wirtinger不等式]],在这个不等式上我们用到过条件$\int_{\mathbb{T}}f(x)\,\nu(x)=0$其中$\nu$是在单位圆周上的单位化了的Haar测度。在Wirtinger不等式的情形中，我们的方法是对函数做傅里叶展开，然后把条件$\int_{\mathbb{T}}f(x)\,\nu(x)=0$理解为其傅里叶系数$\widehat{f}(0)=0$。

因此我们不妨也参考[[Wirtinger不等式]]的方案，来优化$\langle f,Tf \rangle$的上界。

#### 1.3 对函数做傅里叶级数展开

首先对函数做傅里叶计数展开:
$$f(x)=\sum_{\xi\in G}\widehat{f}(\xi)e^{\frac{2\pi i \xi x}{n}}$$
平移以后的函数傅里叶级数展开$$Tf(x)=\sum_{\xi\in G}\widehat{Tf}(\xi)e^{\frac{2\pi i \xi x}{n}}$$其中傅里叶系数(此群上傅里叶系数和傅里叶变换是一样的)$$\widehat{Tf}(\xi)=\widehat{f}(\xi)e^{\frac{2\pi i \xi}{n}}$$于是$$Tf(x)=\sum_{\xi\in G}\widehat{f}(\xi)e^{\frac{2\pi i \xi}{n}}e^{\frac{2\pi i \xi x}{n}}$$考虑到$\chi_{\xi}(x):=e^{\frac{2\pi i \xi x}{n}}$的单位正交性，于是：$$\begin{aligned}\langle f,Tf \rangle&=\left\langle \sum_{\xi\in G}\widehat{f}(\xi)e^{\frac{2\pi i \xi x}{n}},\sum_{\eta\in G}\widehat{f}(\eta)e^{\frac{2\pi i \eta}{n}}e^{\frac{2\pi i \eta x}{n}} \right\rangle \\&= \sum_{\xi\in G} \widehat{f}^2(\xi)e^{\frac{2\pi i \xi}{n}}\end{aligned}$$如果我们对两边取实数部分，并且考虑到$\widehat{f}(0_G)=\int_{x\in G}f(x)\,d\mu(x)=0$于是$$\begin{aligned}\langle f,Tf \rangle&=\text{Re}\left(\sum_{\xi\in G} \widehat{f}^2(\xi)e^{\frac{2\pi i \xi}{n}}\right) \\&= \sum_{\xi\in G} \widehat{f}^2(\xi)\text{Re}(e^{\frac{2\pi i \xi}{n}})\\&= \widehat{f}^2(0_G)+\sum_{\xi\in G,\xi\neq 0_G} \widehat{f}^2(\xi)\cos(\frac{2\pi\xi}{n})\\&= \sum_{\xi\in G,\xi\neq 0_G} \widehat{f}^2(\xi)\cos(\frac{2\pi\xi}{n})\\&\leq \cos(\frac{2\pi}{n})\sum_{\xi\in G,\xi\neq 0_G} \widehat{f}^2(\xi)\end{aligned}$$最后由于Paseval恒等式$\sum_{\xi\in G} \widehat{f}^2(\xi)=||f||_{L^2}^2$于是最终得到Ky Fan不等式的函数版本的结果$$\langle f,Tf \rangle\leq \cos\left(\frac{2\pi}{n}\right)||f||_{L^2}^2$$

* 回顾一下1.2当中分析的$\widehat{f}(0_G)=\int_{x\in G}f(x)\,d\mu(x)=0$这一个条件。其实对比[[Wirtinger不等式]],这个条件倒像是人为添加的，并且二者的联系更是一种巧合。Wirtinger不等式当中，因为需要利用$$\begin{aligned} \hat{f}(n) 
=\frac{T}{2 \pi i n} \hat{f}^{\prime}(n) \end{aligned}$$这个条件做放缩，因此$\hat{f}(0)$就显得很碍事，不妨在条件中令其"消失"。而在Ky Fan不等式当中，因为我们要使用$\cos(\frac{2\pi\xi}{n})\leq \cos(\frac{2\pi}{n})$,而因为$\xi=0_G$的时候是一个例外，既然如此为何不让它"消失"？这就是这两个问题中都要求函数在群的单位元的位置上的傅里叶系数消失的原因。

> [!整个问题的idea]
> 实际上我们的思路的来源是源自于[[在Hilbert空间当中建立坐标系从而简化问题]]这个思路，如果函数涉及到内积，以及$L^2$模，那么我们把函数依照正交基进行分解，就会把函数的问题转换为一些较为初等的简单的操作。Ky Fan不等式的这个证明的处理精神非常类似于[[根据模与内积的信息得到积分不等式]]这个问题。我们把函数做正交分解以后，问题就变成了一个简单的初等的不等式问题。

整个想法包含在[[傅里叶变换与傅里叶展开]]当中。