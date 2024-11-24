---
tags:
  - math
  - 实分析
  - 调和分析
---
#### 1.1 证明的基本想法

整个证明依据三个想法得到:

> [!想法1]
> 与光滑函数做卷积，你也会变得光滑。

根据[[函数卷积的基本性质]]当中的1.6,如果我们可以找到一个光滑函数$h\in C_c^{\infty}$那么如果用它与目标函数做卷积那么我们就会得到一个同样光滑的函数$h*f$。但是这并非是紧支的，因为$f$的支撑未必是紧的。不过转念一想，其实这并不难做出调整。因为我们考虑到[[函数卷积的基本性质]]中的1.4，如果$f$也是紧支的那么卷积以后的结果也是紧支的，但是这并不难办到，因为我们总是对于任意的$\varepsilon>0$,可以找到对$f$的一个截断$f_{\varepsilon}$使得$f_{\varepsilon}$是具有紧支的，并且$$||f-f_{\varepsilon}||_{L^p}<\varepsilon$$如此一来，$$h*f_{\varepsilon} \in C_c^{\infty}$$不过此处其实除了选择$f_{\varepsilon}$为$f$的截断以外还能选择比如$C_c$的函数，因为我们知道$C_c$是函数$f$的稠密子空间。不过从操作上来讲，截断函数要更容易构造一些。

> [!想法2]
> 我们可以构造一个逼近单位元$\{k_{\lambda}\}_{\lambda>0}$，从而让目标函数$f \in L^p$与逼近单位元做卷积，从而得到一个$$||f*k_{\lambda}-f||_{L^p}\xrightarrow{\lambda\to \infty} 0$$

有关性质以及证明可以参考：[[approximate identity]]

结合想法1，2不难发现，我们需要的逼近单位元是有一定的讲究的，我们需要它是光滑的(无限可微)。于是现在我们的目标是找到一个可以做成逼近单位元的，无限光滑的函数。

所以有这样的函数存在吗？有的。

> [!Mollifier(磨光子)的定义]
> 函数$\varphi$是$\mathbb{R}^r$中的一个具有紧支的光滑函数，函数的标准扩展被定义为$$\varphi_{\lambda}(x):=\lambda^r\varphi(\lambda x)$$那么$\varphi$被称之为Mollifier，如果它具有以下两个性质：
> 1. 积分为1：$$\int_{\mathbb{R}^r} \varphi(x)\,dx=1$$
> 2. 它的标准扩展逼近Dirac delta函数：$$\varphi_{\lambda}(x)\xrightarrow{\lambda\to +\infty} \delta(x)$$

回忆[[approximate identity]]的定义,我们不难验证，对于一个积分为1的函数，如果我们对它进行标准扩展，那么我们就会得到一个逼近单位元。现在加上Mollifier当中对函数紧支以及光滑性的要求，那么我们就能得到具有紧支的光滑的逼近单位元。

此外还有一些特殊的Mollifier的额外要求：
* 正磨光子:如果额外要求$\varphi(x)\geq 0$
* 对称磨光子:如果$\varphi(x)=g(|x|)$，并且$g$也是光滑的。

那么真的有具有这样的性质的所谓的磨光子存在吗？

> [!bump函数]
> $$\varphi(x):=\begin{cases}\frac{1}{I_r}e^{\frac{-1}{1-|x|^2}}&\text{|x|} < 1 \\0&|x|\geq 1 \end{cases}$$其中$I_r$与$\mathbb{R}^r$的维度有关，是一个为了让$\varphi$的积分为1的，用来让函数标准化的常数。

从对磨光子的定义上来讲，这是不但是一个磨光子，而且是一个正的，对称的磨光子。

有了这样的函数以后我们就可以完成证明。

### 2. 证明

首先对任意的$\varepsilon >0$都存在一个截断函数$f_{\varepsilon}$其具有紧支集，并且使得$$||f-f_{\varepsilon}||_{L^p}<\frac{\varepsilon}{2}$$现在假设$\varphi(x)$是一个$\mathbb{R}^r$上的bump函数(定义见上文)，也就是一个磨光子，于是我们可以通过它的标准扩展得到$\varphi_{\lambda}(x):=\lambda^r\varphi(\lambda x)$,这是一个光滑的逼近单位元，于是由[[approximate identity]]当中提到的基本性质,对任意的$\varepsilon>0$存在$\varphi_{\lambda_{\varepsilon}}$使得$\varphi_{\lambda_{\varepsilon}}*f_{\varepsilon} \in C_c^{\infty}$（理由参考上文）,并且$$||\varphi_{\lambda_{\varepsilon}}*f_{\varepsilon}-f_{\varepsilon}||_{L^p}<\frac{\varepsilon}{2}$$因此由三角不等式可以,对任意的$\varepsilon>0$存在$\varphi_{\lambda_{\varepsilon}}*f_{\varepsilon} \in C_c^{\infty}$，由三角不等式满足$$\begin{aligned}||f-\varphi_{\lambda_{\varepsilon}}*f_{\varepsilon}||_{L^p}&\leq ||f-f_{\varepsilon}||_{L^p}+||\varphi_{\lambda_{\varepsilon}}*f_{\varepsilon}-f_{\varepsilon}||_{L^p} \\&<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon\end{aligned}$$
因此$C_c^{\infty}(\mathbb{R}^r)$在$L^p(\mathbb{R}^r)$当中稠密。

### 3. 具体的例子

如何用刚才的证明策略去构造一个光滑逼近$\mathbb{R}$上的单位区间$[0,1]$上的特征函数$1_{[0,1]}(x)$的函数列?

首先我们选择一维的bump函数$$\Phi(x):=ae^{-\frac{1}{1-x^2}}1_{[-1,1]}$$其中$1/a=\int_{-1}^{1}e^{-\frac{1}{1-x^2}}dx$。然后我们对其作标准扩展得到函数列$$\Phi_{n}(x)=n\Phi(nx)$$这里注意因为我们的目标函数$1_{[0,1]}(x)$在单位区间上是连续的，并且整体上是有界的，那么由逼近单位元的性质(见[[approximate identity]])，我们知道$$1_{[0,1]}*\Phi_n(x)\rightrightarrows 1_{[0,1]}(x)$$