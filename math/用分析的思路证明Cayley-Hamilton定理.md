---
tags:
  - math
  - 线性代数
---

> [!复数域上的Cayley-Hamilton定理]
> $A$是复数域上的n阶方阵，其特征多项式为$\chi_A$那么$$\chi_A(A)=O$$

我们的想法是基于下面这样两个结果：

> [!引理1]
> $(M_n(\mathbb{C}),||\cdot ||)$复数域上的n阶方阵的赋范数空间，假设全体可对角矩阵矩阵的集合为$D$，那么$D$在范数的意义下是$M_n(\mathbb{C})$的稠密子集。

* 这里没有明确提及具体的矩阵范数，不过由于矩阵范数都可以视为是$\mathbb{C}^{n^2}$这样的有限维向量空间上的范数，而因为有限维向量空间上范数的等价性，因此任何矩阵范数意义下稠密性都不会发生变化。

> [!引理2]
> 假设映射$f,g:X\to Y$是从拓扑空间$X$到$Y$的两个连续映射，其中$Y$是Hausdroff的。如果两个函数$$f(x)=g(x),\forall x\in D$$其中$D\subset X$是一个稠密子集。那么$$f(x)=g(x),\forall x\in X$$

换言之，拓扑空间之间的两个连续映射，只要在一个稠密子集上相等，那么在整个空间上就是完全相等的两个连续映射。（证明可以参考[[确定一个连续实变函数，仅考虑实数的稠密子集上的值就够了]]当中对引理1的证明）

那么我们关于Cayley-Hamilton的整个证明的思路完全是参照[[an epsilon of room]]的想法的。

我们首先假设映射$\chi_M(M)$是把矩阵$M$的特征多项式$\chi_M$作用到$M$上得到一个新的矩阵，相当于是$f_1:M\mapsto \chi_M(M)$的这样一个映射。假设$f_2:M\mapsto O_n$,那么Cayley-Hamilton定理要成立实际上要证明的是$$f_1(M)=f_2(M),\forall M \in M_n(\mathbb{C})$$而要这个结果成立，因为我们知道这两个映射都是连续的，于是按照引理2，我们只需要证明二者在一个稠密子集上成立。而引理1已经告诉我们可对角化的矩阵的集合是$M_n(\mathbb{C})$当中的一个稠密子集，以及Cayley-Hamilton定理显然在可对角化矩阵上成立，于是证明结束。


### 1. 关于细节的补充证明

#### 1.1 证明可对角矩阵的稠密性

因为范数的等价性，所以任何矩阵范数意义下稠密性的结果都是不会改变的。为了计算的方便，我们这里选择Frobenius范数，或者称之为混合范数$L_{2,2}$，假设矩阵$A=(a_{i,j})$那么$$||A||_{F}^2 := \left(\sum_{i,j\leq n}|a_i-a_j|^{2}\right)=\text{trace}(A^{*}A)$$然后我们从Schur分解(参考[[把矩阵转换为标准型从而简化问题]])出发，对于矩阵$A$存在一个酉矩阵$Q$,以及上三角矩阵$T$使得$$A = QTQ^{*}$$现在对$T$的对角线上的元素，也就是矩阵$A$的n个特征按照实部从小到大排列，即$\lambda_k = x_k+iy_k$并且满足$x_1\leq \cdots \leq x_n$。那么对于任意的$\varepsilon$，从各个开区间$I_k=\left(x_k-\sqrt{\frac{\varepsilon}{n}},x_k+\sqrt{\frac{\varepsilon}{n}}\right)$当中都能找到一个$x_k'$使得$x_k'\in I_k$并且$$x_1'<\cdots <x_n'$$于是我们可以找到一个矩阵$A_{\varepsilon} = QT_{\varepsilon}Q^{*}$其中$T_{\varepsilon}$是一个与矩阵$T$除了对角线元素以外其余皆相同的上三角矩阵。其对角线元素组成的集合是$\{x_1'+iy_1,\cdots,x_n'+iy_n\}$,并且按照$T'$的对角线元素的虚部与$T$的对角线元素一致的方式排列。

现在我们宣称$A_{\varepsilon}$就是我们要找的那个使得$$||A-A_{\varepsilon}||_F<\varepsilon$$的可对角化矩阵。因为，首先$A_{\varepsilon}$的特征值彼此不同(实部不同)，因此它可以对角化。其次，因为$T-T_{\varepsilon}$是一个实对角矩阵，因此$(T-T_{\varepsilon})^{*}=T-T_{\varepsilon}$,也就是说是一个自伴矩阵。于是$$\begin{aligned}||A-A_{\varepsilon}||_F^2&=\text{trace}((A-A_{\varepsilon})(A-A_{\varepsilon})^{*})\\&= \text{trace}((T-T_{\varepsilon})(T-T_{\varepsilon})^{*})\\&= \text{trace}((T-T_{\varepsilon})^2)\\&= \sum_{k\leq n} |x_k-x_k'|^2\\&<\sum_{k\leq n} \frac{\varepsilon}{n}=\varepsilon\end{aligned}$$这里用到了迹的性质，详细可以参考[[矩阵的迹与算子的迹的统一]]。

#### 1.2 证明中关键的映射的连续性

整个证明我们都依赖于$$f_1:M\mapsto \chi_M(M)$$这个映射的连续性。

关于这一点，因为$$\chi_M(M)=\sum_{ r=0}^{n} \chi_M^{r} M^{r}$$其中$\chi_M^{r}$是特征多项式$\chi_M(z)$的$r$次项系数。要证明映射$f_1$是连续的，我们只需要证明$\chi_M^{r}$关于变量$M$是连续的即可。

因为矩阵范数的等价性，我们为了方便下面讨论的时候依旧选择Forbenius范数。由[[关于由行列式定义出来的矩阵多项式]]当中2.2当中的公式，特征多项式的系数$\chi_M^{r}$实际上是由$M$的$r$阶主子式的和构成，也就是说如果我们能证明$||A-A_k||_F\to 0$能导出其任意$r$阶主子式的收敛，那么整个问题也就证明完了。而这一点是由于，矩阵依范数收敛必然导致矩阵元素逐个收敛，这是因为$$|A-A_k||_F^2=\sum_{i,j\leq n}|a^{i,j}-a^{i,j}_k|^2\to 0$$因为每一项都非负，因此必然有$$|a^{i,j}-a^{i,j}_k|\to 0$$而关于行列式的Hadamard不等式告诉我们，主子式是收敛的，即$$A_k\begin{pmatrix}i_1,\cdots i_r\\i_1,\cdots i_r\end{pmatrix}\to A\begin{pmatrix}i_1,\cdots i_r\\i_1,\cdots i_r\end{pmatrix}$$于是连续性得证。


