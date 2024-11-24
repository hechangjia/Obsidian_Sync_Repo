---
tags:
  - math
  - 实分析
---
现在有两个$\sigma-\text{finite}$的测度空间$(X,\mathcal{A},\mu)$以$(Y,\mathcal{B},\nu)$在$X \times Y$上定义了一个product measure $\mu \times \nu$那么:

> [!Fubini-Tonelli定理]
> 如果$f$定义在$X \times Y$上是可积的或者函数$|f|$是可测的，那么有$$\int_{X\times
>     Y}f(x,y)\,d(\mu\times\nu) = \int_{X}\left(\int_Y f(x,y) \,
>     d\nu\right) \, d\mu = \int_Y\left(\int_X f(x,y) \,
>     d\mu\right) \, d\nu$$

> [!Fubini-Tonelli定理的一个使用策略]
> 注意到，Tonelli定理只需要要求非负函数是可测函数，并不要求可积。因此有这样的策略:
> 
> 1.  首先使用Tonelli定理计算$|f|$的积分，如果可测的话。如果一切顺利，那么积分是有限的，于是Fubini定理自然成立。
> 2.  如果发现其中一个积分计算出来是无穷的情况，那么自然证明原来的函数$f$并不可积，于是Fubini定理失效。


### 1.  例子1：典型的用法
函数$f$在闭区间$[0,b]$上可积，并定义函数$$g(x)=\int_{x}^{b}\frac{f(t)}{t}dt,\text{
} 0 <x\leq b$$证明函数$g$在闭区间$(0,b]$上可积并且:
$$\int_{0}^{b}g(x)dx = \int_{0}^{b}f(t)dt$$

在交换积分次序之前首先判断函数是否可积,中间因为$\frac{|f(t)|}{t}$可测，所以使用Tonelli定理换序
$$\begin{aligned}\int_{0}^{b}
|g(x)|dx&=\int_{0}^{b}\left|\int_{x}^{b}\frac{f(t)}{t}dt\right|dx\&\leq
\int_{0}^{b}\int_{x}^{b}\frac{|f(t)|}{t}dtdx \\ &=
\int_{0}^{b}\int_{0}^{b}\frac{|f(t)|}{t}\chi_{\{ b\ge t\ge
x>0 \}}dtdx \\
&=\int_{0}^{b}\int_{0}^{b}\frac{|f(t)|}{t}\chi_{\{ b\ge
t\ge x>0 \}}dxdt \\ &= \int_{0}^{b}\int_{0}^{t}
\frac{|f(t)|}{t}dxdt \\ &=
\int_{0}^{b}|f(t)|dt<+\infty\end{aligned}$$所以函数$g$可积，$\frac{f(t)}{t}\chi_{\{b\ge t\ge x>0 \}}$在$0,b]\times[0,b]$上也可积，因此可以使用Fubini定理换序，过程和上面基本一致，最后得到结果:
$$\int_{0}^{b}g(x)dx = \int_{0}^{b}f(t)dt$$

### 2.例子2：函数不可积导致Fubini定理失效
$$f(x,y):=\begin{cases}\frac{x^2-y^2}{(x^2+y^2)^{2}}&(x,y)\in[0,1]^2,(x,y)\not
= (0,0)\\0 &(x,y)=(0,0)\end{cases}$$令$I = [0,1]$，首先函数$|f|$是可测的，因此由Tonelli定理直接交换顺序计算(如果发现不可积，可以稍微放缩):
$$\begin{aligned}\int_{I^2}|f(x,y)|d(x,y) &=\int_{I^2}
\frac{x^2-y^2}{(x^2+y^2)^{2}}\chi_{\{1>x\geq
y>0\}}d(x,y)+\int_{I^2}\frac{y^2-x^2}{(x^2+y^2)^{2}}\chi_{\{0<x<y\leq1\}}d(x,y)\\
&\geq\int_{0}^{1}\int_{0}^{x}\frac{x^2-y^2}{(x^2+y^2)^{2}}dydx
= \int_{0}^{1}\frac{1}{2x}dx = +\infty
\end{aligned}$$因此这个例子当中Fubini定理是不可用的。实际上使用Fubini定理会发现:

1.  $\int_0^1 \left(\int_0^1 \frac{x^2-y^2}{(x^2+y^2)^2} dy\right) dx = \int_0^1 \frac{1}{1+x^2} dx = \frac{\pi}{4}$
2.  $\int_0^1 \left(\int_0^1 \frac{x^2-y^2}{(x^2+y^2)^2} dx\right) dy = - \frac{\pi}{4}$

### 3. 反例2:$\sigma-\text{finite}$条件缺失导致失效

$I =[0,1]$然后令$\mathcal{B}(I)$是Borel代数，令$\mu$是Lebesgue测度，$\nu$是counting measure,现在构建两个测度空间:$(I,\mathcal{B}(I),\mu)$以及$(I,\mathcal{B}(I),\nu)$.

考虑$I^2$当中的一个闭集$D=\{(x,y):x=y,(x,y)\in I^2\}$,那么自然$D\in \mathcal{B}(I^2) = \mathcal{B}(I) \otimes \mathcal{B}(I) \subset \mathcal{B}(I) \otimes \mathcal{P}(I)$现在考虑计算积分
$$\int_{I^2}\chi_{D} d(\mu \times \nu)$$

1.  $\int_{I}\left(\int_{I} \chi_{D}(x,y) d\mu(x)\right)d\nu(y)=\int_{I}0d\nu(y)=0$
2.  $\int_{I}\left(\int_{I} \chi_{D}(x,y) d\nu(y)\right)d\mu(x)=\int_{I}1d\mu(x)=1$

这主要是因为$\nu$是counting measure，所以$(I,\mathcal{B}(I),\nu)$并不是$\sigma-\text{finite}$的测度空间.

### 4. 经典反例3：不可积的例子2

$$f(x,y):=\begin{cases}\frac{1}{y^2}&0<x<y<1\\
-\frac{1}{x^2}&0<y<x<1 \\ 0 &\text{ otherwise}\end{cases}$$
先考虑Tonelli定理,$I=[0,1]$,$$\begin{aligned}\int_I\int_I
|f(x,y)|\,dydx&=\int_I\int_I
\frac{1}{y^2}\chi_{\{0<x<y<1\}}\,dydx + \int_I\int_I
\frac{1}{x^2}\chi_{\{0<y<x<1\}}\,dydx\\&=
\int_{0}^{1}\int_{x}^{1}\frac{1}{y^2}\,dydx+
\int_{0}^{1}\int_{0}^{x} \frac{1}{x^2}\,dydx \\ &\ge
\int_{0}^{1}\int_{x}^{1}\frac{1}{y^2}\,dydx
=\int_{0}^{1}(-1+1/x)\,dx =
+\infty\end{aligned}$$因此显然，函数并不可积，所以Fubini定理是不适用的，因此可以很容易预期：
$$\int_I\int_I f(x,y)dydx \neq \int_I\int_I f(x,y)dxdy $$

### 5. 反例4：求和的版本的反例

$\Omega=\{\ 1,2,3,.....\}$，$\mu$是counting measure，$\mathcal{P}(\Omega)$是幂集。这样可以建立一个可测空$(\Omega,\mathcal{P}(\Omega),\mu)$，然后在$\mathcal{P}(\Omega)\otimes \mathcal{P}(\Omega)$上定义测度$\mu\times \mu$，现在考虑在$\Omega^2$上对函数的积分:
$$f(i,j)=\begin{cases}1&,\text{ if }i=j \ -1&,\text{ if }i=j+1
\ 0&,\text{ otherwise }
\end{cases}$$我们可以把$\Omega^2$看成是一个无限阶的矩阵，那么函数的取值写成矩阵就是:
$$[f(i,j)]=\begin{bmatrix}1&0&0&0&\cdots
\\ -1&1&0&0&\cdots
\\0&-1&1&0&\cdots
\\0&0&-1&1&\cdots
\\\vdots&\vdots&0&-1&\cdots
\\\vdots&\vdots&\vdots&\vdots&\ddots
\\0&0&0&0&\cdots
\end{bmatrix}$$也就是说考虑积分:
$$\int_{\Omega^2}f(i,j)d(\mu\times \mu) =
\sum_{i,j\in\Omega}f(i,j)$$也就是说这实际上就是求和。

这个积分实际上是不积的，因为$\sum_{i,j\in\Omega}|f(i,j)|$实际上并不收敛。这意味着Fubini定理在此处是不适用的，如果一定要尝试，会发现累次积分不一致:

1.  $\int\left(\int f(x,y)\,d\mu(y)\right)d\mu(x)=\sum_{i=1}^\infty \left(\sum_{j=1}^\infty f(i,j)\right)=1$
2.  $\int\left(\int f(x,y)\,d\mu(x)\right)d\mu(y)=\sum_{j=1}^\infty\left(\sum_{i=1}^\infty f(i,j)\right)=0$




