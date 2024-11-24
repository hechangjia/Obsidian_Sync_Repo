---
tags:
  - math
  - tool_idea
---

> [!Borel-Cantelli lemma]
> $(X,\mathcal{F},\mu)$是一个测度空间，$E_1,E_2,E_3,...\in \mathcal{F}$并且满足测度的和收敛，$$\sum_{n\geq 1}\mu(E_n)<\infty$$
> 那么几乎所有$x\in X$都包含在至多有限个$E_n$当中。换句话说，$$\mu(\limsup_{n\to\infty}E_n)=0$$或者说$$\mu\left(\bigcup_{n\geq N}E_n\right)\to0$$

这里最后结果的等价是因为，有这么一个单调增加的集合的包含关系
$$ \limsup_{n\to\infty}E_n\subseteq ...\subseteq \cup_{n\geq 2}E_n \subseteq \cup_{n\geq 1}E_n$$也就是说，$x\in \limsup_{n\to\infty}E_n$即此元素在无穷多个$\{E_n\}$中的集合的交集中。否则的话，一顿存在某个$N$,使得$n>N$的时候$\cup_{n\geq N}E_n$当中不含有元素$x$。而$\limsup_{n\to\infty}E_n$是零测度的集合，这也就意味着，几乎所有$x \in X$只能属于有限个$\{E_n\}$中的元素。也可以表示为$\cup_{n\geq N}E_n\downarrow \limsup_{n\to\infty}E_n$，于是$$\mu(\cup_{n\geq N}E_n)\downarrow \mu(\limsup_{n\to\infty}E_n)=0$$最后的结果有时候也可以表述为，$$\mu\left(\{x:x\in E_n \text{ i.o.}\}\right)=0$$其中$\text{ i.o.}$表示"infinitely often"，表示发生的次数是无穷的，这是$\limsup_{n\to\infty}E_n$这个集合的另外一种解释。那么假设我们令$\text{ f.o.}$表示"finitely often",那么我们可以把集合$X$划分为两个部分：$$X=\{x:x\in E_n \text{ i.o.}\}\cup\{x:x\in E_n \text{ f.o.}\}$$
右边第一个集合是零测度的，第二个集合包含了$X$当中在测度$\mu$的意义下，几乎所有的点。这意味着$X$当中几乎所有点，都只能出现在有限个$E_n$当中。

举个具体例子

> [!例子1]
> $([0,1],\mathcal{B}([0,1]),m)$是一个测度空间，$m$是Lebesgue测度。假设集合$A_n = [0,\frac{1}{n^2}]$,那么因为$$\sum_{n\geq 1} m(A_n)=\sum_{n\geq 1} \frac{1}{n^2}<\infty$$因此$m(x\in A_n \text{ i.o. })=0$。也就是说，$[0,1]$上几乎所有点都只属于有限多个形如$A_n = [0,\frac{1}{n^2}]$的区间，这很显然。其实这里唯一一个属于无穷多个此类区间的点就只有$x=0$这一个点罢了。


### 1. 此lemma在序列的几乎处处收敛上的应用

> [!常用引理1]
> 如果$\forall \varepsilon > 0$,定义集合$A_{n,\varepsilon}:=\{x:|f_n(x)-f(x)|\geq\varepsilon\}$都有
> $$\sum_{n\geq1}\mu(A_{n,\varepsilon})<\infty$$那么可以得到结论
> $$\mu\left(\limsup_{n\to\infty}A_{n,\varepsilon}\right)=0,\forall \varepsilon>0$$于是
> $$f_n(x) \to f(x) \text{ a.e. }x$$

* 下面证明$\mu\left(\limsup_{n\to\infty}A_{n,\varepsilon}\right)=0,\forall \varepsilon>0$可以导出$$f_n(x) \to f(x) \text{ a.e. }x$$
对于固定的$\varepsilon>0$有$$X=\{x:x\in A_{n,\varepsilon} \text{ i.o.}\}\cup\{x:x\in A_{n,\varepsilon} \text{ f.o.}\}$$现在假设$x_0 \in \{x:x\in A_{n,\varepsilon} \text{ f.o.}\}$，这就意味着存在一个$N_{x_0,\varepsilon}$使得对任意$n>N_{x_0,\varepsilon}$有$|f_n(x_0)-f(x_0)|<\varepsilon$于是$$\limsup_{n\to \infty}|f_n(x_0)-f(x_0)|\leq \varepsilon$$现在令$A_{k}:=\{x:x\in A_{n,\frac{1}{k}} \text{ f.o.}\}$，$x_0\in A_k$意味着一定有$$\limsup_{n\to \infty}|f_n(x_0)-f(x_0)|<\frac{1}{k}$$于是只要$x_0 \in \cap_{k\geq 1}A_k$，那么就一定有$$\limsup_{n\to \infty}|f_n(x_0)-f(x_0)|=0$$因此$f_n(x_0)\to f(x_0)$。

那么换言之，如果集合$E$用于表示那些函数列不收敛的点的集合，那么一定有$$E\subseteq \cup_{k\geq 1}A_k^c$$而实际上$A_k^{c}=\{x:x\in A_{n,\frac{1}{k}} \text{ i.o.}\}$,常用引理1告诉我们，$\mu(A_k^c)=0$,那么$\cup_{k\geq 1}A_k^c$也是零测度的。于是$$\mu(E)\leq \mu(\cup_{k\geq 1}A_k^c)=0$$
因此$f_n(x)\xrightarrow{a.e.} f(x)$。



> [!常用引理2]
> $$A_{n}:=\{x:|f_n(x)-f(x)|\geq \varepsilon_n\}$$其中$\varepsilon_n \downarrow 0$，并且同时$$\sum_{n\geq 1}\mu(A_n)<\infty$$
> 于是按照上面同样的做法，如果$x \not \in \limsup_{n\to\infty} A_{n}$那么存在一个$N_x$使得$\forall n >N_x$都有$$|f_n(x)-f(x)|< \varepsilon_n$$同样能表示$f_n(x)\to f(x)$，那么能得到结论，$$f_n(x)\to f(x)$$几乎处处成立。

这两个命题以及类似的证明逻辑**可以用来证明一系列关于函数列几乎处处逐点收敛的命题**：

1. [[函数列几乎处处有界与Borel-Cantelli lemma的应用]]这个例子当中把函数列几乎处处有界的条件转换为了集合与测度的形式，然后精心构造了一个可以适用于Borel-Cantelli引理的结构，从而证明了命题。
2. 

### 2.在概率论当中的应用
#### 2.1 第二Borel-Cantelli引理

在概率论当中集合$A_n$的上极限会被表示为$$\limsup_{n\to\infty}A_n=\{\omega:\omega \in A_n\text{ i.o.}\}$$在考虑这个上确界集合的测度的时候还会进一步简写为$$P(\limsup_{n\to\infty}A_n)=P(A_n \text{ i.o.})$$在概率论的主题当中引入了sigma代数当中两个元素独立的概念，即$A,B \in \mathcal{F}$我们说二者独立，当且仅当$P(A\cap B)=P(A)P(B)$。引入这个概念以后有第二Borel-Cantelli lemma：

> [!The second Borel-Cantelli lemma]
> 集合列$A_1,..,A_n,..\in\mathcal{F}$互相之间是独立的，并且其测度形成的集合不收敛$$\sum_{n\geq 1}P(A_n)=\infty$$
> 那么$$P(\limsup_{n\to\infty}A_n)=P(A_n \text{ i.o.})=1$$

这里因为要证明$P(A_n \text{ i.o.}) =1$而我们知道$P(\cup_{n\geq N}A_n)\downarrow P(A_n \text{ i.o.})$,那么我们实际上就是要证明对于任意的正整数$N$,$P(\cup_{n\geq N}A_n)=1$.反过来也就是要证明$P(\cap_{n\geq N}A_n^{c})=0$。

转换为一个有限问题，最后再做极限处理。
$$\begin{aligned}P\left(\bigcap_{n=M}^{N} A_n^c\right) &= \prod_{n=M}^{N} (1 - P(A_n)) \leq \prod_{n=M}^{N} \exp(-P(A_n)) \\&= \exp\left(- \sum_{n=M}^{N} P(A_n)\right) \to 0 \text{ as } N \to \infty \end{aligned}
$$
这其中用到了独立性的条件，以及使用了$1-x\leq e^{-x}$的放缩。

#### 2.2 把独立性的条件减弱

如果完全没有独立性的条件，那么$\sum_{n\geq 1}P(A_n)=\infty$未必能推出$\limsup_{n\to \infty} A_n$为满测度的集合。但是我们可以把独立性的条件减弱一些，使得我们可以用一个更弱的条件判断$\limsup_{n\to \infty} A_n$是不是满测度。

> [!定量版本的第二Borel-Cantelli引理]
> 集合列$A_1,..,A_n,..\in\mathcal{F}$满足存在一个正实数$C$使得$$\sum_{i,j\leq N}P(A_i \cap A_j)\leq C \left(\sum_{i\leq N}P(A_i)\right)^2$$对无穷多个正整数$N$成立，并且其测度形成的集合不收敛$$\sum_{n\geq 1}P(A_n)=\infty$$
> 那么$$P(\limsup_{n\to\infty}A_n)\geq \frac{1}{C}$$

* 很容易观察到，如果这一列可测集合是相互独立的，那么相当于$C=1$，对任意的正整数$N$都有$$\sum_{i,j\leq N}P(A_i \cap A_j)\leq C \left(\sum_{i\leq N}P(A_i)\right)^2$$从而使得$P(\limsup_{n\to\infty}A_n)\geq 1$,于是$(\limsup_{n\to\infty}A_n)$这是一个满测度的集合。
##### 2.2.1 把无穷的问题转换为有限的问题

我们的目标是得到$\limsup_{n\to\infty}A_n$这个集合的测度的下界估计，根据[[an epsilon of room]]当中版本2的想法，我们转换为对任意的正整数$T,Q$而言$A_{T}^{Q}:=\cup_{n\geq T}^{Q} A_n$也必须满足这样的下界，或者至少$$P(A_{T}^{Q})\geq \frac{1}{C}f(T,Q)$$然后函数$f$满足$$\liminf_{Q\to \infty}\liminf_{T\to \infty}f(T,Q)\geq 1$$这样我们就可以根据$$P(\limsup_{n\to\infty}A_n)=\lim_{Q\to \infty}\lim_{T\to \infty}P(A_{T}^{Q})\geq \frac{1}{C}$$因为$A_{T}^{Q}\uparrow A_T$,当$Q\to \infty$的时候，以及$A_{T}\downarrow \limsup_{n\to\infty}A_n$当$T\to \infty$的时候。

现在经过转换后的问题是有限问题，很多事情都更好进行具体地处理。

##### 2.2.2 利用集合的特征函数
参考[[把集合问题转换为函数问题]]

> [!大致的思路]
> 通过集合的特征函数把集合的问题转换为函数的问题，使用处理函数的工具来分析问题。

考虑函数$G_{T,Q}(x):=\sum_{n=T}^{Q} 1_{A_n}(x)$,此函数具有性质:
1. 函数的积分恰好就是集合测度之和:$$\mathbb{E}(G_{T,Q})=\sum_{n=T}^{Q} \mathbb{E}(1_{A_n})=\sum_{n=T}^{Q} P(A_n)$$
2. 函数$L^2$范数的平方，是集合两两相交的测度的和:$$\begin{aligned}\mathbb{E}(G_{T,Q}^2)&=\mathbb{E}\left(\sum_{T\leq n,m\leq Q} 1_{A_n}(x)1_{A_m}(x)\right)\\&= \sum_{T\leq n,m\leq Q} \mathbb{E}(1_{A_n}1_{A_m})\\&=\sum_{T\leq n,m\leq Q} P(A_n\cap A_m)\end{aligned}$$
3. 提供$P(A_{T}^{Q})$的一个下界。由柯西不等式，我们能得到以上两个结果互相之间的一个关系:$$\mathbb{E}(G_{T,Q})^2=\mathbb{E}(G_{T,Q}\cdot 1_{A_{T}^{Q}})^2\leq \mathbb{E}(G_{T,Q}^2)P(A_{T}^{Q})$$于是$$\begin{aligned}P(A_{T}^{Q})&\geq \frac{\mathbb{E}(G_{T,Q})^2}{\mathbb{E}(G_{T,Q}^2)} \\&=\frac{\left(\sum_{n=T}^{Q} P(A_n)\right)^2}{\sum_{T\leq n,m\leq Q} P(A_n\cap A_m)}\\&\geq  \frac{\left(\sum_{n=T}^{Q} P(A_n)\right)^2}{\sum_{ n,m\leq Q} P(A_n\cap A_m)}\end{aligned}$$
由以上结果，再加上对$A_n$交际测度之和上界的不等式，我们得到$$\begin{aligned}P(A_{T}^{Q})&\geq \frac{\left(\sum_{n=T}^{Q} P(A_n)\right)^2}{\sum_{ n,m\leq Q} P(A_n\cap A_m)}\\&\geq \frac{1}{C}  \frac{\left(\sum_{n=T}^{Q} P(A_n)\right)^2}{\left(\sum_{n\leq Q} P(A_n)\right)^2}\\&=\frac{1}{C}  \frac{\left(\sum_{n\leq Q} P(A_n)-\sum_{n< T} P(A_n)\right)^2}{\left(\sum_{n\leq Q} P(A_n)\right)^2}\end{aligned}$$因为$\sum_{n\geq }P(A_n)$是发散的，因此$\lim_{Q\to \infty}P(A_{T}^{Q})\geq \frac{1}{C}$,因此根据最开始的分析
$$P(\limsup_{n\to\infty}A_n)=\lim_{Q\to \infty}\lim_{T\to \infty}P(A_{T}^{Q})\geq \frac{1}{C}$$

#### 2.2 具体应用

因为概率论相对于一般的测度加入了有限测度,sigma代数当中元素的独立性等等条件，从而可以导出一些更好的结果：
1. 在[[有限测度空间上依测度收敛的等价命题]]这个问题当中，我们首先证明了依照测度收敛的充要条件，其中必要条件是用Borel-Cantelli引理证明的。而这个结论的一个应用告诉我们，在有限测度的意义下，依照测度收敛可以被连续函数保持。
2. [[随机变量期望收敛导出几乎处处收敛的一个条件]]当中我们已知随机变量$X_n$的期望的收敛结果，现在我们需要把结果加强到此随机变量$X_n$几乎处处收敛。此处采用的方法依旧是Borel-Cantelli引理，不过直接对目标进行Chebyshev不等式基础上的逐项估计误差太大，我们采用的是对函数的"值的分布"函数进行了一个类似于三角不等式的放缩，然后再进行进一步的估计，从而达成Borel-Cantelli引理证明几乎处处收敛的要求条件。
3. 在[[Borel-Cantelli lemma证明某种版本下的强大数定律]]当中，我们通过一个额外的关于随机变量$L^4$模存在的条件下，我们先给出随机变量和的平均值$\frac{S_n}{n}$的弱估计的更好的上界。根据这个更好的上界，我们可以得到$$\sum_{n\geq 1} P\left(\left\{\omega:\left|\frac{S'_n(\omega)}{n}\right| >\varepsilon\right\}\right)<\infty$$由此引出Borel-Cantelli lemma，从而根据拓展版本的引理，得到几乎处处收敛的结果，得到所谓的强大数定律。此外第二lemma还在此笔记中证明了强大数定律要成立，期望的有限性是必要条件。特别的类似于这个例子的应用，我们总结在[[加强收敛性质的条件与手段]]当中，即我们可以结合依测度收敛的“集中不等式”与"Borel-Cantelli引理"，从而证明几乎处处收敛。
4. [[Etemadi关于强大数定律的证明]]当中“引理1”的证明当中，我们为了证明截断后的随机变量的和$T_n$在几乎处处收敛的意义下，某种程度等价，即$\frac{T_n}{n}-\frac{S_n}{n}\xrightarrow{a.e.}{0}$,我们利用了截断序列$Y_i$与原本的随机变量$X_i$的一个关系$$P(Y_i\neq X_i \text{ i.o.})=0$$而这是由Borel-Cantelli引理证明的。
5. [[单位区间内10进制小数中含有无数个7的小数的Lebesgue测度为1]]在这个问题当中我们把关于Lebesgue测度的问题转换为概率问题，因为我们知道10进制表示当中每一位数都是独立同分布的$U(\{0,1,...,9\})$的随机变量。然后我们观察到，问题当中说的十进制小数中包含无穷多个7，我们很快想到了这等于是求$P(\omega \in A_k \text{ i.o.})$。这样我们只需要考虑每一位为7的事件的概率，以及这些事件是否独立，而这些条件显然可以被满足，因此考虑使用第二Borel-Cantelli lemma.
6. [[Khintchine定理]]的第一部分，我们需要证明在级数收敛，即$\sum_{q\geq 1}\psi(q)<\infty$的情况下，$\psi$可测的集合，$A_{\psi}:=\{x\in \mathbb{R}:||qx||<\psi(q)\}$是零测度的。问题等价于在单位区间上考虑，即证明$A_{\psi}\cap [0,1]$是零测度的，紧接着发现，我们可以把该集合看成是$$A_{\psi}\cap [0,1]=\limsup_{q\to \infty} E_q$$于是问题转换为后者是零测度的，这很显然可以利用Borel-Cantelli引理来证明，最后问题转换为估计$m(E_q)$。
7. [[Khintchine定理]]的第二部分，


