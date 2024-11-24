---
tags:
  - math
---

> [!Approximate identity(逼近单位)]
> 对于一个$\mathbb{R}^n$上的可积的函数族$K_{\lambda}(x)\in L(\mathbb{R}^n),\lambda>0$:
> 1.  函数积分为1：$\int_{\mathbb{R}^n}K_{\lambda}(x)dx=1$ 
> 2.  函数绝对可积：$\int_{\mathbb{R}^n}|K_{\lambda}(x)|dx\leq A$并且$A$与参数$\lambda$无关。
> 3.  对任意的$\delta>0$，$$\int_{|x|\geq\delta}|K_{\lambda}(x)|dx\to0,\text{as}\lambda\to\infty$$

1. **一个简单的构造途径**：得到这种函数的一个简单办法是由一个绝对可积的，并且在整个$\mathbb{R}^n$上积分为1的函数$K(x)$经由$$K_{\lambda}(x):=\lambda^nK(\lambda x)$$来构成，其中n是由$\mathbb{R}^n$决定的。主要验证第三个条件的满足，此时$$\begin{aligned}\int_{|x|\geq\delta}|K_{\lambda}(x)|dx&= \int_{\mathbb{R}^n} \lambda^n |K(\lambda x)| \chi_{|x|\geq \delta} \,dx \\&= \int_{\mathbb{R}^n} |K(y)|\chi_{|y|\geq \lambda\delta}\,dy \to 0,\text{ as }\lambda \to \infty\end{aligned}$$
第一步是[[积分的伸缩公式]]，第二步的极限是因为积分的绝对连续性，当然也可以直接用收敛定理去说明。

2. **名称的由来**: 

> [!代数]
> 如果给一个线性空间配备一个封闭且具有双线性性的二元运算，那么我们这是一个"代数"(algebra).假设我们用$\cdot :V\times V \to \times V$表示这个具有双线性性的封闭的线性空间$V$上的二元运算，下面称其为乘法，那么
> * **如果乘法满足结合律**:称之为结合代数。即如果$a,b,c \in V$那么$$(a\cdot b)\cdot c = a \cdot (b\cdot c)$$
> * **如果乘法具有单位元**：称之为有单位的代数。也就是说存在一个$I \in V$使得$a \cdot I = a,\forall a \in V$.
> * **如果乘法具有交换律**: 那么称之为交换代数，也就是说$\forall a,b \in V$那么$$a\cdot b = b \cdot a$$

通常来说我们会把$L^{1}(\mathbb{R}^n)/\sim$简称为$L^{1}(\mathbb{R}^n)$,也就是说实际上我们面对的是一个在几乎处处相等的意义下的等价类组成的线性空间。这个线性空间上如果我们给它装备一个由两个函数卷积构成的二元运算，此时$(L^{1}(\mathbb{R}^n),*)$是一个代数，并且二元运算满足交换律和结合律:
1. **封闭性**,也就是说两个可积函数的卷积还是可积的.
这是因为由Fubini-Tonelli定理(具体定理叙述和理解参考[[Fubini-Toenlli定理的例子与反例]])以及Holder不等式可以推出下面的不等式

> [!欧氏空间上卷积的Young不等式]
> $1\leq p,q,r \leq \infty,\frac{1}{p}+\frac{1}{q} = \frac{1}{r} + 1$,那么$$||f*g||_{L^r}\leq ||g||_{L^p}||f||_{L^q}$$

此处只需要令$r=p=q=1$，那么此时就得到$$||f*g||_{L^1}\leq ||g||_{L^1}||f||_{L^1}<\infty$$
于是封闭性就得到了满足。
2. **双线性性**,也就是说$(af+bg)*h=a f*h +b g*h$，另一边也同样满足线性性。这是Lebesgue积分的线性性满足的。
3. **可交换性**,也就是$f*g=g*f$,因为在$\mathbb{R}^d$上Lebesgue测度是具有平移不变性的。
4. **满足结合律**同样由Fubini定理保证。

但是**这个代数没有单位元**！不过呢，我们有近似于单位元的对象存在，也就是逼近单位，也就是说虽然$K_n$不是单位元，但是$f*K_n$收敛到$f$.

### 1. $L^1(\mathbb{R}^n)$当中的逼近单位的常用结论

#### 1.1 常用结论

对于代数$(L^{1}(\mathbb{R}^n),*)$当中的逼近单位$K_{\lambda}$，有下面三个常用的关于逼近的结果:

> [!逼近单位的三个基本结果]
> 1. $f \in L^p(\mathbb{R}^n),1\leq p\leq \infty$，那么$f * K_{\lambda}\in L^p(\mathbb{R}^n)$并且$$||f * K_{\lambda}-f||_{L^p}\to 0,\text{ as }\lambda\to \infty$$
> 2. 如果函数$f$在$\mathbb{R}^n$上一致连续并且有界，那么$f*K_{\lambda}$也是一致连续并且有界的，并且$$f * K_{\lambda}\rightrightarrows f \text{ as }\lambda \to \infty$$
> 3. 如果函数$f$在$\mathbb{R}^n$上有界并且在开集$\Omega\subset \mathbb{R}^n$上连续，那么$f*K_{\lambda}$在$\mathbb{R}^n$上有界且一致连续，此外对于任意的紧子集$D \subset \Omega$都有$$f * K_{\lambda}\rightrightarrows f \text{ as }\lambda \to \infty$$

#### 1.2 对结论1的理解

$(L^p(\mathbb{R}^n),*),1< p\leq \infty$虽然不是一个代数，因为除了$p=1$的时候**其他情况下卷积没办法==总是==保证封闭性**。不过虽然无法总是保证封闭性，但是选一些特殊的对象去和$f$做卷积，还是可以保持封闭性的，比如说如果做卷积的对象是来自于$L^1(\mathbb{R}^n)$当中的逼近单位元，那么Young不等式就可以保证卷积的结果还在$L^p(\mathbb{R}^n)$当中。在这种特殊情况下，对于$1\leq p<\infty$一定有$$||f*K_{\lambda}||_{L^p}\leq ||f||_{L^p}||K_{\lambda}||_{L^1}$$这便保证了卷积这个二元运算在$L^p(\mathbb{R}^n)$当中的封闭性。










对这种函数族还有更强的要求，如果满足我们称其为
-   概念2：更强的条件good family of approximations to the     identity简称为good kernel 1.  函数积分为1：$\int_{\mathbb{R}^n}K_{\lambda}(x)dx=1$2.  函数全局的控制：$K_{\lambda}(x)=O(\lambda^{n})$3.  尾部的控制:$K_{\lambda}(x)=O\left(\frac{1}{\lambda|x|^{n+1}}\right)$-   证明第二个概念的确是比第一个更强的概念-   证明通过积分为1的函数$f(x)$通过$\lambda^n\varphi(\lambdax)=\varphi_{\lambda}(x)$构造出来的函数族是属于第一个定义的，同时如果我们添加条件，比如$f$是有界的并且具有紧支，那么也能符合第二个定义。