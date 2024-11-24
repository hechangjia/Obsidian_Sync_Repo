---
tags:
  - math
  - 实分析
---

> [!问题]
> $f \in L^{\infty}(\mathbb{R}^n)$并且其支集是一个有限可测集，那么$f \in L^p(\mathbb{R}^n),p\geq 1$并且
> 
> $$\lim _{p \rightarrow \infty}\|f\|_p=\|f\|_{L^\infty}$$ 
> 其中$\|f\|_{L^\infty}:=\sup \{r \in \mathbb{R}:\mu(\{x:|f(x)| \geq r\})>0\}$ 也可以定义为
> $||f||_{L^\infty}:=\inf \{r \in \mathbb{R}:\mu(\{x:|f(x)| \geq r\})=0\}$

这个问题的本质是让我们认识到当p增加的时候，这种范数对函数较大的值越来越灵敏，即当p增大的时候范数反应的更多是函数在极值处的行为。

### 1. 证明

从$||f||_{L^\infty}$的定义就可以看出来，$f\leq ||f||_{L^\infty}$几乎处处成立，又因为函数有一个有限测度的支集，那么存在一个有限测度的集合$E$使得，
$$\|f\|_{L^p}=\left(\int_E|f(x)|^p d \mu\right)^{1 / p}
\leq\left(\int_E\|f\|_{L^{\infty}}^p d \mu\right)^{1 / p}
\leq\|f\|_{L^{\infty}} \mu(E)^{1 / p}$$取上极限的话:
$$\limsup_{p \to \infty} ||f||_p \leq
\|f\|_{L^{\infty}}$$
所以整个证明重要的是在另外一边不等式的证明。

根据定义，对任意的$\varepsilon >0$都存在一个$\delta_{\varepsilon}>0$有:$$\mu\left(\left\{x:|f(x)| >\|f\|_{L^{\infty}} -\varepsilon\right\}\right)\geq\delta_{\varepsilon}$$
因为 $\|f\|_{L^\infty}$是这样的集合测度$\mu(\{x:|f(x)|\geq r\})>0$的上确界，那么任意比这个更小的正实数都会使得这样的集合测度为正。于是:
$$\int|f|^pd\mu \geq \delta_{\varepsilon}
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$这里的放缩也是常见的，就是先给出函数在某个集合上满足的不等式，然后整个积分放缩就按照不等式的上界或者下界乘上集合的大小(测度)。$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}} - \varepsilon,\forall \varepsilon
>0$$这也就意味着:
$$\liminf_{p \to \infty} ||f||_p \geq
\|f\|_{L^{\infty}}$$于是极限存在且等于$\|f\|_{L^{\infty}}$.

这里的想法是典型的an epsilon of room的想法:
$||f||_{p} = A(p),B'=\|f\|_{L^{\infty}}$,我们想要证明:
$$A(\infty)\geq B'$$我们入手的点是
$$A(p)\geq B_{\varepsilon}(p)=\delta_{\varepsilon}
^{1/p}(\|f\|_{L^{\infty}} - \varepsilon)$$
然后对p取极限，
$$\liminf_{p\to\infty} A(p)\geq B'-\varepsilon
$$



### 2. 想法的来源

**找下界估计的过程这是受到了Chebyshev不等式的证明的启发(参考[[有限测度下各个收敛之间的关系]])，想要对积分做放缩，可以让被积函数做放缩，不过同时要给出使得这样的放缩成立的集合的测度的估计。** 根据[[分段估计的想法]]当中提到的最基本的"底乘以高"的想法，也就是说对于非负函数的积分，如果我们可以找到被积函数的下界估计，那么积分的下界就可以是下界乘以此集合的测度。

> [!简单的想法]
> 在测度空间$(X,\mathcal{F},\mu)$上的某个有限测度的集合$E$上对有下界为$M$的非负函数$f$求积分，那么一个非常粗略的积分估计就是$$\int_{E}f\,d\mu \geq M\mu(E)$$

但是通常的情况会稍微复杂一点，比如说，虽然集合$E$当中很多值都是的函数大于等于M,但这并非全部，那么此时我们只需要修改一下这个估计。
> [!对简单想法的调整]
> 在测度空间$(X,\mathcal{F},\mu)$上考虑一个有限测度的集合$E$，以及一个非负且$E$上可积的函数$f$.子集$E_{r}\subseteq E$被定义为$$E_{M}:=\{x:f(x)\geq M\}$$那么对函数$f$在$E$上的积分的一个非常粗略的估计就是$$\int_{E}f\,d\mu \geq M\mu(E_M)$$


### 3.紧集上的连续函数

此外如果$f\in C(E)$,其中$E$是一个紧集。那么上述命题中，无穷范数实际上就是一致范数，也就是函数的最大值。对于连续函数而言，如果不引入无穷范数，命题可以叙述为:

> [!连续版本的命题]
> $f\in C(E)$,其中$E$是一个$\mathbb{R}^n$的紧子集并且在Lebesgue测度m下是有限测度,假设函数在此集合上的模的最大值为$M$,那么$$\lim _{p \rightarrow \infty}\|f\|_p=M$$

同样的证明考虑$E_{\varepsilon}:= \{x:|f| >M-\varepsilon\}$,然后由于$$\int|f|^pd\mu \geq m(E_{\varepsilon})
(\|f\|_{L^{\infty}} -
\varepsilon)^p$$
于是和上面一样的论断，得到$$\liminf _{p \rightarrow \infty}\|f\|_p\geq M-\varepsilon$$
但是这里有一个问题，是否对于任意$\varepsilon>0$都有$m(E_{\varepsilon})>0$？会不会有某个$\varepsilon$使得其等于0，这样上面的证明就失去意义了。答案是不会，因为$f$是连续的。

$E_{\varepsilon}=|f|^{-1}((M-\varepsilon,\infty))$,这是一个开区间关于连续映射$|f|$的原像，那么也是一个开集。作为一个欧氏拓扑下开集，其内部必然包含一个开球，如果这个开集是0测度的，那么其必然是空集。否则其内部包含一个半径不为0的开球，而这个开球的Lebesgue测度不会是0，这导致矛盾。

因此，如果这个集合是0测度的，那么它就是空集。这意味着$E$当中所有元素都使得$|f|$小于$M-\varepsilon$，这与$M$是$|f|$在$E$上的最大值矛盾。