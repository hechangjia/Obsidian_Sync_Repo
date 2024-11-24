---
tags:
  - math
  - 解析数论
---
### 1. 证明序列$\eta_n$在$[0,1]$当中稠密

> [!问题]
> 证明，序列$\eta_n = \left\{\frac{n}{2\pi}\right\}$形成的集合作为$[0,1]$区间当中的稠密子集。

针该问题的证明，其中一个思路是可以用过Weyl判别去证明一个加强版本的命题，即证明其均匀分布。(参考[[模1均匀分布于Weyl判别]])

不过我们还可以通过丢番图逼近的想法来证明这件事，也就是kronecker的定理。

> [!kronecker定理]
> 对于给定的无理数$\alpha$，以及$\forall \beta\in\mathbb{R}$，任意$\varepsilon > 0$那么存在正整数$q$以及整数$p$使得$$|q\alpha-p-\beta|<\varepsilon$$

这是对丢番图逼近里的Dirichlet定理的推广(的一个一维版本)，因为如果$\beta=0$，那么这就是Dirichlet定理：

> [!Dirichlet定理其中一种形式]
> 对于无理数$\alpha$以及任意的$\varepsilon>0$存在一对互素的整数$q,p$其中$q>0$使得$$|q\alpha-p|<\varepsilon$$

---

对于这个问题，令$\alpha=\frac{1}{2\pi}$,这是一个无理数，对于$\forall \beta\in(0,1)$我们固定一个足够小的$\varepsilon$，那么由Kronecker定理知道存在一对整数$p,q$使得$$q\alpha-p\in (\beta-\varepsilon,\beta+\varepsilon)\subset(0,1)$$

**此问题解决的关键是注意到$\eta_n=\{n\alpha\}= n\alpha - \lfloor n\alpha\rfloor,n\geq1$这样的序列所形成的集合可以定义为$$E_{\alpha}=\{a\alpha-b\in(0,1) :a\geq 1,b\geq 0\}$$**
关于上面的集合当中元素的一些基本特征:
1. 如果$\alpha$是无理数，那么没有任何两个元素是相同的。因为如果$\{n\alpha\}=\{m\alpha\}$,那么一定有:$$\alpha
    = \frac{\lfloor n\alpha\rfloor - \lfloor
    m\alpha\rfloor}{n-m}$$这样的话，这个数一定是有理数。
2. 如果我们让$q_0$固定，那么对于$q_0\alpha-p\in E_{\alpha}$.其实只有唯一的一个$p_0 = \lfloor q_0\alpha\rfloor$,因为如果有不同的$p_1$，那么二者的差距至少是$|p_0-p_1|\geq1$，如此一来另一个必然不在$E_{\alpha}$当中。
3. 如果$h\in E_{\alpha}$并且$0<kh<1$，那么$kh \in E_{\alpha}$。比如假设$\alpha = e$,我们发现$\{10e\}\approx 0.1828$,然后$2\{10e\} \approx0.3656$实际上，它的结果也就是$\{20e\}$.

接下来证明$$E_{\alpha}=\{\eta_n:n\geq 1\}$$
$\{\eta_n:n\geq 1\}\subseteq E_{\alpha}$没有问题，关键是反过来是否成立。其关键在于，任意$a\alpha -b \in E_{\alpha}$必然存在一个整数$N$使得$\eta_{N}=a\alpha -b$.令$a =N$,那么必然$\lfloor N\alpha\rfloor=b$.如果不相等，因为二者皆为整数，因此两个数的绝对值至少为1，那么就不可能都落在$(0,1)$当中。

那么上面满足kronecker定理的$q\alpha-p \in E_{\alpha}$,这意味着集合$E_{\alpha}$在$(0,1)$当中是稠密的。

**所以这个问题可以等价于，如何证明kronecker定理。**


### 1. 经由Dirichlet定理证明Kronecker定理

针对一维的特殊形式的Kronecker定理，可以经由Dirichlet定理来证明。


1.  由Dirichlet定理，不失一般性对于任意给定的无理数 $\alpha>0$存在一对整数$p,q$使得$$|q\alpha-p|<\varepsilon$$也就是说有一对$p,q$使得$q\alpha-p \in(-\varepsilon,\varepsilon)$如果其为负数，我们可以通过乘上-1使得落在$(0,\varepsilon)$当中。因此Dirichlet定理保证了对于任意的$\varepsilon>0$都存在一个$E_{\alpha}$当中的元素落在$(0,\varepsilon)$当中。
2.  假设为$h$就是落在$(0,\varepsilon)$当中的集合$E_{\alpha}$当中的元素(意味着$h<\varepsilon$),那么$(0,1)$可以被分割为$(0,h],(h,2h],...,(nh,1)$个区间。而如果我们任选一个$\beta\in(0,1)$那么此元素必定落在其中某个区间当中,假设是第$k$个区间，而由于每个区间的长度最多不过$h$,于是$$|kh-\beta|<h<\varepsilon$$而因为$h\in E_{\alpha}$具有形式$h = q_0\alpha-p_0$，然后如果$0<kh<1$的话其必然$kh\in E_{\alpha}$.
3.  这意味着$\forall \beta \in (0,1)$以及任意$\varepsilon > 0$，存在一个$E_{\alpha}$当中的元素$kh=q'\alpha-p'$使得$$|q'\alpha-p'-\beta|<\varepsilon$$这意味着$E_{\alpha}$的稠密性。
4. 这个结果不难推广到$\beta \in \mathbb{R}$当中去。

### 2. 证明Dirichlet定理

证明基于[[鸽笼原理]].

首先证明一个形式：

> [!Dirichlet定理表述2]
> $\alpha$是无理数，对于任意正整数$n$存一个有理数,存一对互素的整数$p,q$其中$0<q\leq n$使得$$0<|q\alpha-p|<\frac{1}{n}$$

不失一般性，假设$\alpha>0$,我们证明存在一对互素的正整数$(p,q)$满足命题中的不等式，也就是说对于任意正整数$n$,$$E_{\alpha}=\{a\alpha-b\in(0,1) :a\geq 1,b\geq 0\}$$这个集合当中至少有一个元素落在$(0,\frac{1}{n})$当中。

整个证明使用一个简单的组合学中的策略，称之为[[鸽笼原理]]或者称之为抽屉原理。

我们可以把$(0,1)$等分为$n$份，分别是:$$(0,\frac{1}{n}),[\frac{1}{n},\frac{2}{n}),...,[\frac{n-1}{n},1)$$如果我们从$E_{\alpha}$当中选取$n+1$个元素，比如前n+1个元素即$$\{1\alpha\},\{2\alpha\},...,\{(n+1)\alpha\}$$那么因为区间只有n个，那么必然有两个元素落在同一个区间当中，这意味着这两个元素的"距离"小于$\frac{1}{n}$。因为$\alpha$是无理数，所以这两个元素是不可能相等的，于是不妨假设这两个元素就是$q_1\alpha-p_1>q_2\alpha-p_2$,那么$$0<|(q_1-q_2)\alpha-(p_1-p_2)|<\frac{1}{n}$$于是$(q_1-q_2)\alpha-(p_1-p_2)\in (0,1/n)$。因为是前n+1个元素当中某两个元素做差，于是我们还知道$0<(q_1-q_2)\leq n$。

---

#### 2.1 Dirichlet定理其他等价叙述

最后如果给定任意正实数$\varepsilon$，那么只要令$n_{\varepsilon}=\lfloor\frac{1}{\varepsilon}\rfloor+1$，那么上面的命题可以改造为$$|q\alpha-p|<\varepsilon$$并且$0<q\leq n_{\varepsilon}$。


当然我能还可以把定理的形式修改为

> [!Dirichlet定理叙述3]
> 对于无理数$\alpha$存在无数多对整数p,q(要求互素，这样才有唯一性。$q>0$)使得$$|\alpha-\frac{p}{q}|<\frac{1}{q^2}$$

详细证明可以参考[[无理测度的定义以及基本的命题]]其中的1.2。

#### 2.2 Wolfram代码

我们可以按照下面的Wolfram代码找到符合条件的Dirichlet定理当中的$p,q$：

```wolfram
(*定义{x}函数*)
f[x_] := x - Floor[x];
(*通过While循环结构，不断筛选{ka},直到落入到区间(0,1/n)*)
k = 1;
While[True, If[f[k*a] < 1/n, Break[], k++]];
(*这里的k就是我们要找的q*)
Print[k]
(*这就要找的p*)
Print[Floor[ka]]
```















