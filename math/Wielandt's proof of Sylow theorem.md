---
tags:
  - math
  - 代数基础
---

> [!Sylow定理中关于p群数目的定理(1872)]
> $G$是一个$n$阶有限群,$p$是一个素数，$r$是一个自然数。那么如果$p^r || n$记此群中Sylow $p$子群的数目为$N_p$，那么$$N_p \equiv 1 \text{ mod }p$$

* 这里的$p^r || n$的意思是，$p^r|n$但是$p^{r+1}$不是$n$的一个因子。或者说$r$是$n$的形如$p^a$的因子当中最大的一个。
* 这里的Sylow $p$子群指的是群的阶数为$p$的幂次的群的子群。
* 这个定理可看成是[[Sylow定理的特例：柯西定理]]的一个推广。因为柯西定理相当于此处$r=1$的情况，此时该群的$p$子群只有可能是$p$阶的群，否则就违反了Lagrange定理。此外Sylow定理告诉我们$p$子群是一定存在的，否则的话就无法满足$N_p \equiv 1 \text{ mod }p$的结果。

整个证明的方法依旧是把群作用在合适的集合上，然后通过群的作用来揭示群的结构。参考[[Groups, as men, will be known by their actions]]。

假设$|G|=p^rm$,构造$X:=\{A\subseteq G:|A|=p^r\text{ and }1_G\in A\}$,群作用定义为$$g\cdot A:=\{ga:a\in A\}$$那么现在，我们需要确定$A\in X$能使得$A\leq G$的集合有多少个，因为这样的子群一定就是我们想要找的$p^r$阶子群。那么现在就需要知道，满足$A\leq G$的集合有什么性质。

* 首先无论$A$是不是子群，都有:$\text{Stab}_G(A)\subseteq A$
因为如果假设$g \in \text{Stab}_G(A)$,那么由于$g\cdot A=A$，以及$1_G\in A$,那么$g1_G=g\in A$，于是$$\text{Stab}_G(A)\subseteq A$$
* 子群与作用的稳定子的关系:
$$A\leq G \iff \text{Stab}_G(A)=A$$首先如果$A\leq G$,那么如果假设$g\in A$于是$gA=A$这表明$A\subseteq \text{Stab}_G(A)$于是我们知道$$A\leq G\implies \text{Stab}_G(A)=A$$反过来如果$\text{Stab}_G(A)=A$，假设$g\in \text{Stab}_G(A)$,那么对于任意$a,b\in A$我们可以找到一个$g$使得$ga=b$,于是$g=ba^{-1}\in A$于是$A\leq G$所以$$\text{Stab}_G(A)=A\implies A\leq G$$
* 稳定子的性质与轨道长度的关系:
$$\text{Stab}_G(A)=A\iff |\text{orb}_G(A)|=m$$这一点可以由轨道稳定子定理得到，参考[[轨道稳定子引理与群的置换表示]]。
* 不能构成子群的$A$对应的轨道长度:其轨道长度一定是被$pm$整除的。
因为$\text{Stab}_G(A)\subseteq A$,所以$|\text{Stab}_G(A)|\leq p^r$。由轨道稳定子引理，$$|\text{orb}_G(A)|=\frac{p^{r}m}{|\text{Stab}_G(A)|}$$轨道长度一定是$p^rm$的一个因子，即具备$p^sm$的形式。如果$A$不是子群，那么由于$|\text{Stab}_G(A)|<|A|=p^r$,于是$|\text{orb}_G(A)|>m$。那么此时轨道长度一定具备$p^sm$的形式，并且$s>0$。于是我们知道此时的轨道长度一定是被$pm$整除的。

综上所述，集合$X$在群作用下划分为了一条条轨道，其中那些能构成$G$的$p^r$阶子群的集合对应的轨道的轨道长度为$m$,其余的长度能被$pm$整除。那么不妨假设长度为$m$的轨道为$N_p$条，于是$$|X|\equiv N_pm \text{ mod }pm$$
为了得到$N_p$的同余关系，我们需要再找一个关于$|X|$的模$pm$的同余方程，这样就可以结合两个同余方程，得到$N_p$的同余关系。

现在我们从$|X|$的元素个数出发，我们发现实际上$$|X|=\binom{p^rm}{p^r}$$我们可以证明上面的组合数满足$$|X|\equiv m\text{ mod }pm$$所以结合两个同余方程，我们知道$$N_pm\equiv m \text{ mod }pm$$于是我们得到了$$N_p \equiv 1\text{ mod }p$$

