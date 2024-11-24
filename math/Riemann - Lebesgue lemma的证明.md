---
tags:
  - math
  - 实分析
  - 调和分析
---
### 1. $\mathbb{R}^n$中的版本

> [!傅里叶变换版本的lemma]
> 如果$f \in L^1(\mathbb{R}^n)$,其傅里叶变换:
> $$\hat{f}(\xi) = \int_{\mathbb{R}^n}f(x)e^{-2\pi i x \cdot \xi } dx$$那么$$|\hat{f}(\xi)|\to 0 \text{ as } |\xi| \to \infty$$
> 因为[[可积函数的傅里叶变换是连续的]]，那么这个命题实际上就是证明$$f \in L^1(\mathbb{R}^n) \implies \hat{f} \in C_0(\mathbb{R}^n)$$

#### 1.1 尝试紧支的连续的函数$C_c(\mathbb{R}^n)$
* **为何只需要证明紧支连续函数的情况即可?**
首先考虑连续的版本，因为如果一旦连续的版本是成立的，那么一定可以推广到可积的函数。
因为对于任意的$\varepsilon >0$,存在一个紧支的连续函数$g$使得，$||f-g||_{L^1} < \varepsilon$,从而: $$ \begin{aligned}|\hat{f}(\xi)| &\leq
\left|\int_{\mathbb{R}^n}(f(x)-g(x))e^{-2\pi i x\cdot
\xi}\right|+|\hat{g}(\xi)| \\ &\leq ||f-g||_{L^1} +
|\hat{g}(\xi)| = \varepsilon +
|\hat{g}(\xi)|\end{aligned}$$
两边取上极限得到，$\limsup_{|\xi|\to+\infty}|\hat{f}(\xi)| \leq \varepsilon ,\text{ for any}\varepsilon > 0$
* **如何证明连续的情形?**

这里以 $n =2$为例子,每个分量都平移$\frac{1}{4\xi_i}$,于是
$$\hat{g}(\xi) =
\int_{\mathbb{R}^2}g\left(x_1+\frac{1}{4\xi_1},x_2+\frac{1}{4\xi_2}\right)e^{-2\pi i x\cdot \xi }e^{-\pi i}dx$$于是
$$|\hat{g}(\xi)| \leq
\frac{1}{2}\int_{\mathbb{R}^2}\left|g(x_1,x_2)-g\left(x_1+\frac{1}{4\xi_1},x_2+\frac{1}{4\xi_2}\right)\right|
dx $$

这里使用到一个与傅里叶变换有关的一个常用的技巧"平移然后制造出差".

总之这样就得到了一个差: 因为函数是具有紧支的,因此$\left|g(x) -g\left(x + h_{\xi}\right)\right|$这部分是有界的，因此使用控制收敛的话当$||h_{\xi}|| \to 0$，可以证明$|\hat{g}(\xi)|\to 0$。（其中$h_{\xi}=(\frac{1}{4\xi_1},\frac{1}{4\xi_2})$）

#### 1.2 使用更强的光滑紧支的函数逼近

我们知道$C_c^{\infty}(\mathbb{R}^n)$是$L^1(\mathbb{R}^n)$的稠密子空间(证明可以参考[[紧支光滑函数在Lp空间当中稠密]])，而假设我们要用$f_{\varepsilon}\in C_c^{\infty}(\mathbb{R}^n)$去逼近$f \in L^1(\mathbb{R}^n)$，我们需要首先保证$f_{\varepsilon}$的傅里叶变换$\widehat{f_{\varepsilon}}$是满足命题的。


由于函数的光滑性，以及光滑函数傅里叶变换与偏微分之间的关系
$$\widehat{f}(\xi)=\frac{1}{2\pi i
\xi_i}\mathcal{F}\left(\frac{\partial}{\partial
x_i}f_{\varepsilon}(x)\right)$$
而等式右边是对一个光滑函数的偏微分作傅里叶变换，这自然是一个有界的函数，那么如此一来就不难发现$$|\widehat{f_{\varepsilon}}(\xi)|\to 0$$
于是现在考察$$\begin{aligned}|\hat{f}(\xi)| &\leq
|\hat{f}(\xi)-\hat{f}_{\varepsilon}(\xi)|+|\widehat{f_{\varepsilon}}(\xi)|
\\ &\leq
||f-f_{\varepsilon}||_{L^1}+|\widehat{f_{\varepsilon}}(\xi)|
< \varepsilon
+|\widehat{f_{\varepsilon}}(\xi)|\end{aligned}$$那么$$\limsup_{|\xi|\to\infty}|\hat{f}(\xi)|
\leq \varepsilon$$
#### 1.3 关于此引理的一些说明

-   综合上面的说法:$\hat{f}\in C_0$
-   对于一般性的$f \in L^1(\mathbb{R}^n)$,不能给出比$|\hat{f}(\xi)|= o(1)$更精确的渐进

因为对于任意的$\varepsilon >0$,都存在一个 $f \in L^1(\mathbb{R}^n)$的函数其傅里叶变换是:

$$\hat{f}(\xi) =
\frac{1}{(1+|\xi|^2)^{\varepsilon}}$$所以对于一般的可积函数，不能给出渐进的一般的结果，不同的函数其傅里变换衰减的速度都是不一样的。

-   傅里叶变换不一定可积的例子:

$$f(x):=1_{[-1,1]}(x)$$其傅里叶变换为:
$$\hat{f}(\xi)=\int_{\mathbb{R}} f(x) e^{-2 \pi i x \xi} d
x=\int_{-1}^1 e^{-2 \pi i x \xi} d x=2 \frac{\sin (2 \pi
\xi)}{2 \pi \xi},\xi \neq 0$$如果$\xi =0,\hat{f}(0) = 2$.

这个时候会发现其傅里叶变换后的函数，并不是一个在$\mathbb{R}$上可积的函数。


-   想要让傅里叶逆变换有意义,需要保证$\hat{f}(\xi)$是可积的。

在这样的条件下,
$$f(x) = \int_{\mathbb{R}^n}\hat{f}(\xi)e^{2\pi i x \cdot
\xi } d\xi,\text{ for a.e. }x $$

#### 1.4 第一种做法的本质

事实上我们只需要首先说明,对函数做一小段平移，那么平移后的函数与平移之前的函数在$L^1$范数的意义下误差很容易控制。

 >[!命题1]
> $f \in L^1(\mathbb{R}^n)$对任意$a\in \mathbb{R}^n$定义$T_a(f):=f(x-a)$，那么$$||T_{a+h}(f)-T_a(f)||_{L^1} \to 0$$当$||h|| \to 0$。

同样的思路我们可以首先证明这个性质对紧支的连续函数$g \in C_c(\mathbb{R}^n)$成立，然后通过稠密性过渡到对于所有可积函数成立。

首先对于任意的$\varepsilon >0$以及给定的$f \in L^1(\mathbb{R}^n)$都存在$g_{\varepsilon} \in C_c(\mathbb{R}^n)$使得$||f-g_{\varepsilon}||_{L^1}<\frac{\varepsilon}{3}$。那么此时由于Lebesgue测度的平移不变性，$$||T_a(f)-T_a(g_{\varepsilon})||_{L^1}<\frac{\varepsilon}{3}$$
接着借助三角不等式，$$\begin{equation}\begin{aligned}||T_{a+h}(f)-T_a(f)||_{L^1}&\leq ||T_{a+h}(f)-T_{a+h}(g_{\varepsilon})||_{L^1}+||T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1}\\ &+||T_{a}(g_{\varepsilon})-T_{a}(f)||_{L^1}\\&<\frac{2\varepsilon}{3} + ||T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1}\end{aligned} 
\end{equation}$$

对于$g_{\varepsilon} \in C_c(\mathbb{R}^n)$的函数而言其本身是一个在$\mathbb{R}^n$上一致连续的函数，因为函数在紧支集$K_{\varepsilon}$上一致连续，而紧支集外函数恒等于0。
$$\begin{aligned}|T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1}&= \int_{\mathbb{R}^n} |g_{\varepsilon}(x-a+(-h))-g_{\varepsilon}(x-a)|\,dm(x) \\ &\leq 2||T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_u m(K_{\varepsilon})\end{aligned}$$
后面这个积分可以被函数$g_{\varepsilon}$的支撑的测度给控制起来，假设其支撑为$K_{\varepsilon}$，这是一个紧集，它是有界闭集，因此有有限的Lebesgue测度。$|g_{\varepsilon}(x-a+(-h))-g_{\varepsilon}(x-a)|$不为0的集合，一定是被集合$K_{\varepsilon} +a$以及$K_{\varepsilon} +a+ h$给覆盖的，而平移不改变Lebesgue测度。

那么在固定地$\varepsilon$的情况下，对于具有紧支集的连续函数$g_{\varepsilon}$是否成立命题1的性质呢？显然是成立的，因为函数一致连续，所以当$||h||\to 0$的时候$||T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_u\to 0$.

于是对上面的三角不等式取上极限得到:
$$\limsup_{||h||\to 0}||T_{a+h}(f)-T_a(f)||_{L^1} \leq \frac{2\varepsilon}{3}$$
以上式子对任意正实数$\varepsilon$成立，因此极限存在且等于0.

* **这里后面取极限的操作是为了避免讨论"两套$\delta-\varepsilon$"的符号避免混乱。**
1. 首先对于任意给定的紧支上连续的函数$g$都有，对任意的正实数$r>0$使得存在一个同时与函数本身的选择，以及正实数$r$有关的参数$\delta_{r,g}$使得所有$h\in B_{\delta_{r,g}}(0)$都有$$||T_{a+h}(g)-T_a(g)||_{L^1}<r$$
2. 然后在这个逼近问题当中，令$r = \frac{\varepsilon}{3}$以及$g=g_{\varepsilon}$那么按照上面的命题，就会存在一个只与$\varepsilon$有关的参数$\delta_{\varepsilon} = \delta_{\varepsilon,g_{\varepsilon}}$使得所有$h\in B_{\delta_{\varepsilon}}(0)$都有$$||T_{a+h}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1} < \frac{\varepsilon}{3}$$
3. 所以最后我们会说，对于任意$\varepsilon>0$都存在球$B_{\delta_{\varepsilon}}(0)$使得所有$h\in B_{\delta_{\varepsilon}}(0)$都有$$|T_{a+h}(f)-T_a(f)||_{L^1}<\varepsilon$$

---

* 特别的，当$a=0$的时候上面的情况变成了对于任意$\varepsilon >0$存在球$B_{\delta_{\varepsilon}}(0)$使得所有$h\in B_{\delta_{\varepsilon}}(0)$都有$$||T_{h}(f)-f||_{L^1}<\varepsilon$$这相当于是一致连续性的类比，只不过把一致范数替换为了$L^1$范数。
* 当我们说，平移算子$T_a$连续的时候，我们指的是$\mathbb{R}^n\times L^1(\mathbb{R}^n)\to L^1(\mathbb{R}^n)$这个映射在第一个变量上是连续的，如果保持第二个变量也就是$f$不变的话。

这个结果可以用来在做差的时候达到和1.1的证明中利用连续函数的差一样的效果。

1.1的证明是利用对平移后的函数做傅里叶变换，发现其平移后的傅里叶变换和原来的傅里叶变换之间相差一个$e^{-2\pi i h_{\xi}}$也就是说$$\begin{aligned}\widehat{T_{h_{\xi}}(f)} &= \int_{\mathbb{R}^n} f(x-h_{\xi})e^{-2\pi i x\cdot\xi}\,dm(x)\\ &=\int_{\mathbb{R}^n} f(y)e^{-2\pi i (y+h_{\xi})\cdot\xi}\,dm(x) \\ &= e^{-2\pi i \xi\cdot h_{\xi}}\int_{\mathbb{R}^n} f(y) e^{-2\pi i y\cdot\xi}\,dm(x) \\ &= e^{-2\pi i \xi\cdot h_{\xi}}\widehat{f}(\xi)\end{aligned}  $$
而我们有$|\widehat{T_{h_{\xi}}(f)} - \widehat{f}(\xi)|\leq ||T_{h_{\xi}}(f)-f||_{L^1}<\varepsilon$当$h_{\xi}\in B_{\delta_{\varepsilon}}(0)$ 当$|\xi| > M_{\varepsilon}$的时候。

这样一来实际上我们只需要保证$|1-e^{-2\pi i h_{\xi}}| > a>0$就行。因为这样我们就可以断言$$|\hat{f}(\xi)| < \frac{\varepsilon}{a}$$
整理一下思路，只要我们可以保证对任意的$\varepsilon >0$存在$M_{\varepsilon}>0$使得任意$|\xi| > M_{\varepsilon}$都存在一个$h_{\xi}\in B_{\delta_{\varepsilon}}(0)$,使得$|1-e^{-2\pi i h_{\xi}}| > a>0$.这一点在1.1的证明里面我们选择的是$h_{\xi}=(\frac{1}{2n\xi_1},...,\frac{1}{2n\xi_n})$使得$|1-e^{-2\pi i h_{\xi}}| =2>1$.（更一般的情况下我们可以参考3.2的引理1）

### 2. $\mathbb{T}$上的版本

> [!傅里叶系数版本]
> $f \in L^1(\mathbb{T})$那么$|\hat{f}(n)|\to 0$具体来说:
> $$\hat{f}(n) =
> \frac{1}{2\pi}\int_{-\pi}^{\pi} f(x)e^{-inx} dx \to 0 \text{
> as } |n| \to \infty$$

#### 2.1 使用简单函数逼近可积函数

* **为何可以这样做?**
$$|\hat{f}(n)| \leq ||f-g_{\varepsilon}||_1 +
|\hat{g_{\varepsilon}}(n)| < \varepsilon + o(1)$$即
$$\limsup_{|n|\to +\infty} |\hat{f}(n)|<\varepsilon
,\forall \varepsilon \implies |\hat{f}(n)|\to 0$$

那么想要完成这个不等式，首先由逼近的条件$\varepsilon >0$存在$g_{\varepsilon}(x)$是一个step function,
$$g_{\varepsilon}(x) = \sum_{k=0}^{l-1}a_k
\mathbf{1}_{E_k}(x),E_k = (x_i,x_{i+1})$$其中$-\pi = x_0 < ...< x_{l-1}=\pi$是对区间的一个划分。

像这种先逼近然后求极限的问题当中使用$\varepsilon -\delta-N$的语言，是要把变量控制到只剩一个n。虽然说$g_{\varepsilon}$是跟随$\varepsilon$变化的，但是当$\varepsilon$被固定下来以后，这个函数也会被固定，最终只有$n$是变量。

-   估计$\hat{g_{\varepsilon}}(n)$

我们要称step function $g_{\varepsilon}(x)$是更简单的函数，并且用更简单的函数逼近，那么其傅里叶系数的模应该是更简单更好估计的，否则一切都是白费力气。
$$|\hat{\mathbf{1}}_{E_k}(n)| = \frac{1}{n}\left|
e^{-inx_{k+1}}- e^{-inx_{k}}\right|\leq \frac{2}{n}$$所以说:

$$\begin{aligned}|\hat{g_{\varepsilon}}(n)| &= \left|\sum
_{k} a_k \hat{\mathbf{1}}_{E_k}(n)\right| \\&\leq \sum_{k}
|a_k\hat{\mathbf{1}}_{E_k}(n)| \\ &\leq \sum_{k}
\frac{2|a_k|}{n}\end{aligned}$$这里只要$\varepsilon$被固定下来，那么$g_{\varepsilon}(x)$就会被固定下来，从而整个求和是一个有限求和，因此
$$|\hat{g_{\varepsilon}}(n)| = O\left(\frac{1}{n}\right)$$
因此
$$|\hat{f}(n)| < \varepsilon + O\left(\frac{1}{n}\right)$$

### 3. 任意局部紧的交换群$G$上的版本

#### 3.1 局部紧的交换群上的傅里叶变换

如果$G$是一个局部紧的交换群(以下简称LCA群)，那么我们可以在$G$的基础上定义一个测度空间$(G,\mathcal{B}(G),\mu)$，其中$\mu$是Haar测度。此测度空间上的可积函数组成的线性赋范空间记为$L^1(G)$. 考虑$G$的Pontryagin对偶群$\hat{G}$,即所有$G\to \mathbb{T}$的连续同态映射构成的群，将成为对偶群。

那么在以上设定下，傅里叶变换$\mathcal{F}$实际上是一个$L^1(G)\to C_0(\hat{G})$的线性泛函。其中$C_0(\hat{G})$表示在无穷远处消失的定义在对偶群$\widehat{G}$上的连续函数组成的空间，具体来说可以定义为，对任意$\varepsilon >0$存在一个紧子集$K_{\varepsilon}\subset \hat{G}$使得对所有$\chi \not\in K_{\varepsilon}$都有$|g(\chi)|<\varepsilon$。

具体来说

> [!一般意义下的傅里叶变换]
> 函数$f\in L^1(G)$的傅里叶变换$\mathcal{F}(f)$可以被定义为,对任意$\chi \in \hat{G}$，$$\mathcal{F}(f)(\chi):=\int_{G} \overline{\chi(g)} f(g) \,d\mu(g)$$

在这样的设定下$\mathcal{F}(f) \in C_0(\hat{G})$就是一般意义下的Riemann-Lebesgue引理。

> [!Riemann-Lebesgue引理]
> 定义在$L^1(G)$上的傅里叶变换$\mathcal{F}$是一个$$L^1(G)\to C_0(\hat{G})$$的线性泛函。

1. 当$G = \mathbb{R}^n$其对偶群$\widehat{\mathbb{R}}^n \simeq \mathbb{R}^n$.于是乎，这个定理就是上面2提到的$L^{1}(\mathbb{R}^n)$版本的R-L引理。
函数$f \in L^{1}(\mathbb{R}^n)$其傅里叶变换可以定义为:
$$\mathcal{F}(f)(\chi_{\xi}) = \int_{\mathbb{R}^n}f(x)\overline{\chi_{\xi}(x) }dm(x) = \int_{\mathbb{R}^n}f(x)e^{-2\pi i x \cdot \xi } dm(x)$$
* 其中测度$m$是欧氏空间当中定义的Lebesgue测度，其当然是一个Haar测度，同时因为Haar测度在局部紧的拓扑群上具有唯一性(精确到相差一个正系数)因此选择哪系数对应的Haar测度来定义傅里叶变换是人为的选择。我们通常会做一个规范化的处理，通常是为了让公式看起来更为简单。
* 关于记号的问题:
首先可以把对偶群$\widehat{\mathbb{R}}^n$当中的元素给表示出来,$$\widehat{\mathbb{R}}^n =\{\chi_{\xi}(x)=e^{2\pi i \xi\cdot x }:\xi \in \mathbb{R}^n\}$$这个表达式实际上传递出此拓扑群与$\mathbb{R}^n$同构，这其中自然就蕴含着拓扑空间$\widehat{\mathbb{R}}^n$与$\mathbb{R}^n$之间的同胚。于是当我们谈到其傅里叶变换$\mathcal{F}(f)(\chi_{\xi})$的时候我们还可以定义一个$\mathbb{R}^n$上的函数$$\hat{f}(\xi):=\mathcal{F}(f)(\chi_{\xi})=\mathcal{F}(f)\circ h(\xi)$$此时我们说$\hat{f}\in C_0(\mathbb{R}^n)$。这里面$h: \xi \mapsto \chi_{\xi}$是一个$\mathbb{R}^n \to \widehat{\mathbb{R}}^n$的同胚映射。

我们可以把这个过程抽象一下：

> [!命题2]
> 拓扑空间$X$与拓扑群$Y$同构，即存在一个同胚映射$h:Y \to X$。现在假设$f\in C_0(X\to \mathbb{C})$那么$g = f\circ h \in C_0(Y\to \mathbb{C})$.

这个命题的关键就在于这个同胚映射$h$.按照上文中对"无穷远处消失"的拓扑的定义，因为$f\in C_0(X\to \mathbb{C})$那么对于任意$\varepsilon>0$一定存在$K_{\varepsilon} \subset X$使得如果$x \not \in K_{\varepsilon}\subset X$那么$|f(x)|<\varepsilon$。那么取$T_{\varepsilon} =h^{-1}(K_{\varepsilon})$，此时因为$h$是同胚映射，因此其逆映射存在且是连续的，由于紧集在连续映射下的像也是连续的，因此$T_{\varepsilon}\subset Y$是一个紧子集。此时因为同胚映射的关系，$h(Y - T_{\varepsilon}) =X - K_{\varepsilon}$因此如果$y\not \in T_{\varepsilon}$那么$h(y)=x \not \in K_{\varepsilon}$这表示$g = f \circ h \in C_0(Y)$.

---
那么同样的道理$\hat{f}(\xi)=\mathcal{F}(f)\circ h(\xi) \in C_0(\mathbb{R}^n)$.

2. 当$G = \mathbb{T}$其对偶群$\hat{\mathbb{T}} \simeq \mathbb{Z}$.于是乎，这个定理就是上面2提到的$L^{1}(\mathbb{T})$版本的R-L引理。

同样的道理，如果$f \in L^1(\mathbb{T})$那么函数的傅里叶变换就是
$$\begin{aligned}\mathcal{F}(f)(\chi_n)&=\int_{\mathbb{T}}f(z)\overline{\chi_n(z)}\,d\mu(z) \\ &= \int_{\mathbb{T}} f(z)z^{-n} d\mu(z) \\ &= \int_{-\pi}^{\pi}f(e^{ix})e^{-inx} \frac{dm(x)}{2\pi} \end{aligned}$$

其中$\mu$是单位圆周上的Haar measure它被定义为从$(\mathbb{R},\mathcal{B}(\mathbb{R}),m)$到$(\mathbb{T},\mathcal{B}(\mathbb{T}),\mu)$的经由映射$r:x \mapsto e^{ix}$给出的pushforward测度，$\mu(A) = \frac{1}{2\pi}m(r^{-1}(A))$.


#### 3.2 LCA群上R-L引理的证明

下面证明LCA群版本的黎曼勒贝格引理。整个证明照搬1.4的证明，只不过把所有内容做了推广。

首先我们应该把命题1，也就是$L^1$空间当中有关平移的命题给推广到LCA群$L^1(G)$上来。

> [!命题3：命题1在LCA群上的推广]
> $G$是一个LCA群$f \in L^1(G)$对任意$a\in G$定义$T_a(f):=f(a^{-1}x)$。那么对于任意$\varepsilon >0$存在单位元$1_G$的邻域$U_{\varepsilon}$使得所有$h \in U_{\varepsilon}$都有$$||T_{ah}(f)-T_a(f)||_{L^1(G)}<\varepsilon$$


整个证明和1.4当中命题1一样，我们考虑到$L^1(G)$是建立在Haar测度之上的，因此$C_c(G)$是此空间的稠密子空间(只需要Radon测度即可)，因此只需要证明$g\in C_c(G)$拥有此性质。

和1.4当中一样，首先得到$$|T_{ah}(g)-T_a(g)||_{L^1(G)}\leq \int_{G} |g(h^{-1}a^{-1}x)-g(a^{-1}x)|\,d\mu(x)$$
由于$g$的一致连续性，同时函数具有紧支集$K_g$，由于Haar测度同时也是Radon测度，于是紧子集的测度是有限的(和1.4一样的讨论)。于是对于任意的$r >0$以及函数$g$存在$1_G$的邻域$U_{r,g}$使得所有$h \in U_{r,g}$都有$$||g(h^{-1}a^{-1}x)-g(a^{-1}x)||_u<\frac{r}{2\mu(K_g)}$$
因此$$|T_{ah}(g)-T_a(g)||_{L^1(G)}< 2\mu(K_g)\frac{r}{2\mu(K_g)}=r$$

然后根据1.4类似的三角不等式得到
$$\begin{equation}\begin{aligned}||T_{ah}(f)-T_a(f)||_{L^1(G)}<\frac{2\varepsilon}{3} + ||T_{ah}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1(G)}\end{aligned} 
\end{equation}$$
于是我们令$r= \frac{\varepsilon}{3},g=g_{\varepsilon}$从而存在$1_G$的邻域$U_{r,g}=U_{\varepsilon}$使得$$||T_{ah}(g_{\varepsilon})-T_a(g_{\varepsilon})||_{L^1(G)}<\frac{\varepsilon}{3}$$对任意$h\in U_{\varepsilon}$成立。于是我们得到结论,对于任意$\varepsilon >0$存在单位元$1_G$的邻域$U_{\varepsilon}$使得所有$h \in U_{\varepsilon}$都有$$||T_{ah}(f)-T_a(f)||_{L^1(G)}<\varepsilon$$

---


取$a = 1_G$那么该结果得到推论，对于任意$\varepsilon >0$存在单位元$1_G$的邻域$U_{\varepsilon}$使得所有$h \in U_{\varepsilon}$都有$$||T_{h}(f)-f||_{L^1(G)}<\varepsilon$$
下面还会用到另一个引理:

> [!引理1]
> 对于LCA群$G$当中单位元$1_G$的任意邻域$U$存在$K \subseteq \hat{G}$使得如果$\chi \in \hat{G} - K$那么存在$x \in U$使得$\text{Re}\chi(x)\leq 0$.

---

整个证明的精神和$G = \mathbb{R}^n$以及$G = \mathbb{T}$的时候并没有太大的区别。本质上是观察到：
* 函数位移$h$然后再做傅里叶变换，新的傅里叶变换不过是原来变换乘以$\overline{\chi(h)}$,即:
$$\begin{aligned}\mathcal{F}(T_h(f))(\chi) &= \int_G f(h^{-1}x)\overline{\chi(x)}\,d\mu(x) \\ &= \int_G f(y)\overline{\chi(hy)}\,d\mu(y)\\ &= \overline{\chi(h)}\mathcal{F}(f)(\chi)\end{aligned}$$
* 如果我们对函数做一个很小的$h$的位移，它的傅里叶变换和原来相差微乎其微，基本可以忽略。
$$\begin{aligned}|\mathcal{F}(T_h(f))(\chi)-\mathcal{F}(f)(\chi)|&\leq \int_G |T_h(f)-f|\,d\mu \\ &=||T_{h}(f)-f||_{L^1(G)}<\varepsilon\end{aligned}$$
* 如此一来这段小位移$h$只要可以保证$|\overline{\chi(h)} -1|$有某种下界比如说$r>0$，也就是保证这个对象不要为0，就可以下结论$$|\mathcal{F}(f)(\chi)| < \frac{\varepsilon}{|\overline{\chi(h)} -1|}< \frac{\varepsilon}{r}$$
* 引理1其实保证了$|\overline{\chi(h)} -1|\geq 1$.
首先什么是小位移?在一般的赋范空间里面，我们会说其范数足够小。注意到赋范空间是一个向量空间，其中本身也是一个拓扑群，这种情况下如果我们说$||h||$足够小，其实就是说$h$是这个群的单位元的邻域当中。因此**在当前的语境下，对于一个LCA群$G$当中足够小的位移其实指的是群$G$的单位元$1_{G}$的邻域。** 而这样的邻域由lemma1可以保证，存在一个$\hat{G}$的紧子集，紧子集的补集里面的元素$\chi$都存在邻域中一个元素，也就是一个小位移$h$使得$\text{Re}\chi(h)\leq 0$.这保证了$|\overline{\chi(h)} -1|\geq 1$.

综上所述，对于任意的$\varepsilon >0$由于$T_x(f)$在$x = 1_G$处的连续性($L^1$范数)那么必定存在$1_G$的一个邻域$U_{\varepsilon}\subseteq G$使得$\forall x$,$$||T_{h}(f)-f||_{L^1(G)}<\varepsilon$$
那么由lemma1我们对于这样的$U_{\varepsilon}\subseteq G$一定存在一个对偶群$\hat{G}$当中的紧子集$K_{\varepsilon}$，满足如果$\chi \in \hat{G}-K_{\varepsilon}$必定存在一个$h \in U_{\varepsilon}$使得$|\overline{\chi(h)} -1|\geq 1$

那么现在正如上面分析的一样$$|\mathcal{F}(f)(\chi)| < \frac{\varepsilon}{|\overline{\chi(h)} -1|}< \varepsilon$$
于是这便是函数属于$C_0(\hat{G})$的定义，于是定义在$L^1(G)$上的傅里叶变换$\mathcal{F}$是一个$L^1(G)\to C_0(\hat{G})$的线性泛函。

---

