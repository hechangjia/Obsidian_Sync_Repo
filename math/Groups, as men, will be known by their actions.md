---
tags:
  - math
  - tool_idea
---

> [!群作用的定义]
> $G$是一个群，$X$是一个集合，如果一个映射$$\alpha:G\times X\to X$$满足关系:
> 1. 关于单位元：$$\alpha(1_G,x)=x$$
> 2. 兼容性：$$\alpha(g,\alpha(h,x))=\alpha(g\cdot h,x)$$
> 则称$\alpha$是群$G$关于集合$X$的一个左群作用。

* 如果关于$\alpha$的兼容性的条件改成$\alpha(\alpha(h,x),g)=\alpha(x,g\cdot h)$那么这就是一个右群作用。

> [!核心想法]
> 让群作用在合适的集合上，能揭露出许多关于群结构的有用信息。

### 1. 群作用在自身上


#### 1.1 左乘
群$G$中的元素$g$，通过左乘的方式作用在群所在集合$G$的某个元素$x$上，得到$G$当中一个新的元素$g\cdot x$。用映射来表示这个作用可以写成$$\alpha(g,x)=g\cdot x$$这里的"$\cdot$"表示群$G$中定义的二元运算。

* $\alpha$的确是一个群作用：
1. 关于单位元：$$\alpha(1_G,x)=1_{G}\cdot x=x$$
2. 兼容性：$$\alpha(g,\alpha(h,x))=\alpha(g,h\cdot x)=g\cdot(h\cdot x)=(g\cdot h)\cdot x=\alpha(g\cdot h,x)$$
* $\alpha$是faithful的群作用，即$$\alpha(g,x)=x,\forall x \in G\implies g=1_{G} $$这意味着任意$x\in G$对应的稳定子$\text{Stab}_x=\langle 1_G\rangle$，那么由轨道稳定子定理(参考[[轨道稳定子引理与群的置换表示]])$x$所在的轨道$\text{orb}_x$的长度恰好为$|G|$，这也就意味着在此群作用下，一共就一条轨道。


典型的例子就是Cayley定理：

> [!Cayley定理,1854]
> 任意$n$阶有限群$G$都同构于对称群$\text{Sym}(G)$的某个子群。

因为$\alpha$是一个群作用，那么固定一个$g\in G$我们可以定义出一个集合$G$的置换：$$\phi_g:x\mapsto \alpha(g,x)$$进而得到一个$G\to \text{Sym}(G)$的群同态：$$\psi:g\mapsto \phi_g$$而此处的群作用$\alpha$的特殊之处在于它使得$\psi$一定是单射。因为我们可以考察$\text{ker}(\psi)$。假设$g \in \text{ker}(\psi)$,那么这意味着$$\psi(g)=\phi_g=1_{\text{Sym}(G)}$$这意味着对任意$x \in G$都有$\phi_g(x)=x$,也就是说$\alpha(g,x)=x$,而$\alpha$是faithful的群作用，于是$g=1_G$。所以其实$\text{ker}(\psi)=\langle 1_G\rangle$,因此$\psi$是一个单射。那么群的第一同构定理（参考[[第一同构定理]]）告诉我们$$\begin{aligned}G\cong G/\langle 1_G\rangle=G/\text{ker}(\psi)\cong \text{im}(\psi)\leq \text{Sym}(G)\end{aligned}$$
#### 1.2 共轭

### 2. 构造群作用

> [!想法1]
> 当我们想要找群$G$的一个满足特定条件的正规子群$H$的时候，我们可以考虑根据群的结构的信息来产生一个群同态，使得同态核就是我们要找的正规子群。而群同态的产生就可以来自于合适的群作用。

* [[证明有限群存在一个满足特定Index条件的正规子群]]

> [!想法2]
> 如果我们想要找到群$G$中包含某个特定性质的元素$a$。我们可以构造一个与群$G$以及其所在集合有关联的群作用(一个群+一个集合)，然后把特定元素$a$的存在性问题转换为群作用下的不动点存在问题。然后我们通过一些手段，得到不动点的数量的下界的估计，从而证明不动点的存在性。

* [[Sylow定理的特例：柯西定理]]