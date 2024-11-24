---
tags:
  - math
  - 实分析
  - 概率论
---
### 1. Kantorovich不等式的不同版本

1.  离散版本(**скалярная версия**):$p_i \geq 0$,同时$0<a\leq x_i \leq b$那么$$\left(\sum_{i=1}^{n}
    p_ix_i\right)\left(\sum_{i=1}^{n} \frac{p_i}{x_i}\right)\leq
    \frac{(a+b)^2}{4ab}\left(\sum_{i=1}^{n}
    p_i\right)^2$$更容易理解的形式可以表达为,令$q_i =\frac{p_i}{\left(\sum_{i=1}^{n} p_i\right)} \geq 0$，并且满足$\sum_{i=1}^nq_i = 1$，于是$$\left(\sum_{i=1}^{n}
    q_ix_i\right)\left(\sum_{i=1}^{n}
    q_i\frac{1}{x_i}\right)\leq \frac{(a+b)^2}{4ab}$$
2.  二次型的版本(версия квадратичной формы):$A$是n阶对称的正定矩阵，其特征值的最大值为$b$,最小值为$a>0$，于是$$\langle{Ax,x}\rangle
    \langle{A^{-1}x,x\rangle}\leq
    \frac{(a+b)^2}{4ab}||x||^4$$换为更容易理解的形式是,$y =\frac{x}{||x||}$,即单位向量，于是$$\langle{Ay,y}\rangle
    \langle{A^{-1}y,y\rangle}\leq \frac{(a+b)^2}{4ab}$$
3.  实积分的版本(версия действительного интеграла): 函数$f \in L^2([0,1]\to \mathbb{R})$,并且函数的值满足$0<a\leq f(x) \leq b<\infty,\forall x \in [0,1]$，那么$$\left(\int_{[0,1]} f(x) dx\right)
    \left(\int_{[0,1]} \frac{1}{f(x)} dx\right) \leq
    \frac{(a+b)^2}{4ab}$$
### 2.以上的版本都可以通过概率的版本进行统一

> [!概率版本的Kantorovich不等式]
> $X$是概率空间$(\Omega,\mathcal{F},P)$上的一个平方可积的随机变量($EX^2 < \infty$)，并且$0<a\leq X(\omega) \leq b<\infty,\forall \omega \in\Omega$，那么成立下面的有关期望的不等式:$$E[X]E[1/X] \leq
>     \frac{(a+b)^2}{4ab}$$

#### 2.1 
离散的版本作为一个特殊情况:

首先定义样本空间$\Omega = \{1,...,n\}$,然后此时sigma代数其实就是此集合的幂集。然后定义概率测度，即一个非负的$\mathcal{F}\to \mathbb{R}$的映射,满足$$P(\{i\}) =
    q_i$$并且满足可列可加性，这样就可以轻松满足$P(\Omega) = 1$这个条件。最后需设计一下随机变量，令随机变量$$X(i) =
    x_i$$这样设计的话，期望可以写作$EX]=\left(\sum_{i=1}^{n} q_ix_i\right)$以及$E[1/X]=\left(\sum_{i=1}^{n} q_i\frac{1}{x_i}\right)$,因此便得到了离散版本的不等式。

#### 2.2 二次型版本

二次型的版本作为一个特殊的情况:

首先定义对于对称矩阵而言，其一定可以对角化，因此不失一般性可以考虑矩阵$A= \text{diag}\{\lambda_1,...,\lambda_n\}$，然后$y =(y_1,...,y_n)$是$\mathbb{C}^n$当中的单位向量，那么$$\braket{Ay,y}
    = \sum_{i=1}^n\lambda_i |y_i|^2,\braket{A^{-1}y,y} =
    \sum_{i=1}^n\lambda_i^{-1}
    |y_i|^2$$此时只需要利用离散版本的不等式的结论即可。
#### 2.3 实积分版本

实积分的版本作为一个特殊的情况:

首先定义样本空间$\Omega =[0,1]$,然后此时sigma代数通常取实数的Borel代数。(因为这样可以直接用实数上的标准拓扑，方便讨论一些与拓扑性质有关的分析问题).最后此时的概率测度就是Lebesgue测度，因为其本身就满足可列可加性以及$\mu(\Omega)= \mu([0,1])=1$。于是此时$$E[f]=\left(\int_{[0,1]} f(x)
    d\mu\right),E[1/f]=\left(\int_{[0,1]} \frac{1}{f(x)}
    d\mu\right)$$于是显然成立。



### 3. 概率版本的证明
#### 3.1 转换为对方差的控制

1.  首先$E[X]E[1/X]$这个对象从哪里冒出来的?

首先能直接想到的就是Cauchy不等式，可以直接给出$E[X]E[1/X] \geq1$,然而我能要找的是这个对象的上界。这个上界来自于Cauchy不等式的另外的一个变形:$$\begin{aligned}|\text{Cov}(X,Y)|&=|E\left[\left(X -
    E[X]\right)\left(Y - E[Y]\right)\right]| \\&\leq
    \left(E\left[\left(X - E[X]\right)^2\right]\right)^{1/2}
    \left(E\left[\left(Y - E[Y]\right)^2\right]\right)^{1/2}
    \\ &= V(X)^{1/2}V(Y)^{1/2}
    \end{aligned}$$这是一个相当常见的不等式，即随机变量的协方差的平方会被各自方差和的乘积给控制起来。协方差写开来就是$|\text{Cov}(X,Y)| = |E(XY)-E(X)E(Y)|$,此时令$Y = 1/X$,由于$EX]E[1/X] \geq1$,那么左边去掉绝对值，最后不等式变成了$$E[X]E[1/X] -1\leq
    V(X)^{1/2}V(1/X)^{1/2} $$现在的问题是如何控制方差。

#### 2.2 如何控制方差

2.  **控制方差**:对于一个平方可积的任意随机变量$Z$，其方差(另一种等价的方式)可以定义为$$V(Z)
    := \inf_{s \in \mathbb{R}}
    [E(Z-s)^2]$$即我们可以把期望视作是Hilbert空间$L^2(\Omega,\mathcal{F},P)$上的线性算子，并且如果令$W$是其中的常函数的子空间,那么期望可以视为一种$L^2 \to W$的正交投影。这很容易验证因为,
* **幂等**：作为$L^2\to L^2$的线性算子，对于任意$X\in L^2$都有$$E(E(X))=E(X)$$
* **自伴随**：验证$\langle E(X),Y\rangle =\langle X,E(Y)\rangle$非常容易，因为实际上$$\begin{aligned}\langle E(X),Y\rangle&=\int E(X)Y\,dP \\&= E(E(X)Y)\\ &= E(X)E(Y) =\langle X,E(Y)\rangle \end{aligned}$$
于是我们可以把空间分解为,$L^2=W\oplus W^{\perp}$.假设我们要求$$\inf_{s\in W}||Z-s||^2$$我们可以把随机变量做一个分解$Z = E(Z)+Z'$后者$Z' \in W^{\perp}$也就是一个期望为0的随机变量。那么$$\begin{aligned}||Z-s||^2 &= ||(E(Z)-s)+Z'||^2 \\&= ||E(Z)-s||^2+||Z'||^2 \geq ||Z'||^2 \end{aligned}$$
也就是说，其下确界为$||Z'||^2 =||Z-E(Z)||^2 =V(Z)$

---

那么按照这个道理$$V(X) \leq E\left(X -
    \frac{a+b}{2}\right)^2 \leq
    \left(\frac{b-a}{2}\right)^2$$$$V(1/X) \leq E\left(1/X - \frac{1/a+1/b}{2}\right)^2 \leq
\left(\frac{b-a}{2ab}\right)^2$$何在一起便得到了最终的形式。

#### 2.3 用上述思路证明一个类似的不等式

> [!Kantorovich不等式的变体]
> $X,Y$是概率空间$(\Omega,\mathcal{F},P)$上的一个平方可积的随机变量($EX^2 <  \infty$)，并且$0\leq a\leq X(\omega),Y(\omega) \leq b<\infty,\forall \omega \in\Omega$，那么成立下面的有关期望的不等式:$$E[X]E[Y] \leq
>     \frac{(b-a)^2}{4}$$

如同上面Kantorovich不等式类似的道理，我们可以借助柯西不等式来使用方差控制协方差，于是$$|\text{Cov}(X,Y)|\leq V(X)^{1/2}V(Y)^{1/2}$$那么如果我们能控制方差也就能控制协方差。而按照上面地分析，在$L^2$当中任意的随机变量$Z$其方差可以被理解为$$V(Z)
    := \inf_{s \in \mathbb{R}}
    [E(Z-s)^2]$$这就意味着对于任意的实数$s$而言，$V(Z)\leq E(Z-s)^2$,等号只有在$s=E(Z)$的时候取到。而此时如果我们令$s = \frac{a+b}{2}$,那么因为$X\in [a,b]$于是$$V(X)\leq E\left(X-\frac{a+b}{2}\right)^2\leq \frac{(b-a)^2}{4}$$同样的道理对$Y$也适用。于是$$|\text{Cov}(X,Y)|\leq V(X)^{1/2}V(Y)^{1/2}\leq \frac{(b-a)^2}{4}$$等号成立当且仅当$E(X)=E(Y)=(b+a)/2$。