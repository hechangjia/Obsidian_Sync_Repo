---
tags:
  - math
  - 调和分析
  - 代数基础
---

> [!L^2空间的定义]
> 设群$G$是一个有限交换群，$L^2(G\to \mathbb{C})$是全体满足$$\int_{G}|f(x)|^2\,d\mu(x):=\frac{1}{|G|}\sum_{x\in G}|f(x)|^2<+\infty$$的函数组成的线性赋范数空间，其范数定义为$$||f||_{L^2}:=\left(\frac{1}{|G|}\sum_{x\in G}|f(x)|^2\right)^{1/2}$$

* 原本$L^2$这个术语是起源于Lebesgue积分，其中的L就表示Lebesgue。最早的时候其实特指$L^2(\mathbb{R}^d)$即定义在$\mathbb{R}^d$上的函数其平方关于Lebesgue测度的积分是有限的。后来在分析学中，人们从Lebesgue测度推广得到了抽象测度，使得我们可以定义在任意的测度空间上的平方可积的函数构成的线性赋范空间。再然后为了推广傅里叶分析的理论，在抽象调和分析当中人们定义出了Haar测度的概念(参考[[圆周上的函数的傅里叶展开]]的1.2节)，这种测度使得我们可以在一般的拓扑群上建立起类似于$\mathbb{R}^d$上的Lebesgue测度类似的傅里叶分析的理论。而此处的$L^2(G\to \mathbb{C})$当中的积分所采用的Haar测度实际上是一个单位化了的计数测度，比如任意可测集合即群$G$的子集$E$的测度$\mu(E)$就被定义为$$\mu(E)=\frac{|E|}{|G|}$$要在拓扑群上进行建立傅里叶分析的理论按理说只需要找到一个haar测度即可，并且局部紧的交换群上的Haar测度互相之间也就是相差一个系数而已，为什么一定要单位化呢？这是因为单位化以后，测度空间$(G,\mathcal{B}(G),\mu)$就可以当成一个概率空间来考虑了，这不仅简化了一些计算同时也为分析一些涉及概率的问题提供便利。

> [!L^2作为一个Hilbert空间]
> $L^2(G\to \mathbb{C})$实际上是一个有限维的内积空间，内积定义为$$\langle f,g\rangle:=\int_{G}f(x)\overline{g(x)}\,d\mu(x)$$或者也可以写成和的形式$$\langle f,g\rangle:=\frac{1}{|G|}\sum_{x\in G}f(x)\overline{g(x)}$$
* 为什么说此空间是有限维的? 
因为我们可以给出此空间的一个简单的基$$\delta_g(x):=\begin{cases}1&x=g\\0&\text{otherwise}\end{cases}$$那么自然对任意的$f \in L^2(G)$我们都可以将其表示为$$f(x)=\sum_{i=1}^{|G|}f(g)\delta_g(x)$$这很显然，因为毕竟$f(G)$是至多$|G|$个不同的复数构成的一个有限集合。并且很容易验证$\{\delta_g:g\in G\}$是线性无关的，因此这是一组基。而基向量的个数是$|G|$，这也就意味着$L^2(G)$此时是一个$|G|$维的内积空间。

既然是一个Hilbert空间那么自然会想要问，这个空间上的一组==好的==单位正交基是什么？特别是对于一些常见的群，如果我们可以把对应的$L^2(G)$的单位正交基具体表示出来，那么我们就可以对此空间中的函数做依照单位正交基做分解。

> [!群特征与对偶群]
> 假设$\widehat{G}$是由$G$的所有特征$$\chi:G\to S^1$$即群$G$到单位圆周的群同态组成的集合。我们可以用复数的乘法定义特征之间的一种二元运算$$\chi_1(x)\chi_2(x):=(\chi_1\cdot \chi_2)(x),\forall x\in G$$而这种运算是封闭的，有单位元的(平凡的特征，把所有群元素映射为$1$),可逆的($\chi$的逆元就是$\overline{\chi}$),于是$\widehat{G}$构成一个群，称之为群$G$的对偶群（庞特里亚金对偶）。

### 1. 傅里叶展开

#### 1.1 $L^2(G)$的单位正交基

群特征在$L^2(G)$当中的一个重要性质是：

> [!命题2.1]
> 有限交换群$G$其对偶群$\widehat{G}$当中的元素能构成$L^2(G)$的单位正交基。

这个事儿我们得分几个步骤来说明：
1. 首先我们要说明，$\widehat{G}$当中的不同的元素是正交的。
2. 其次我们要验证$|\widehat{G}|=|G|$。这一步我们甚至可以得到更强的结论，$\widehat{G}\simeq G$。

如果以上两件事都可以被验证，同时结合上文$L^2(G)$作为Hilbert空间定义的部分下面的注解，我们相当于找到了$|G|$个单位正交的元素，而这一定是一组基（很容易验证一定是线性无关的），因此就证明了这是一组单位正交基。

> [!引理2.1]
> $G$是有限交换群,那么其对偶群$\widehat{G}$当中的不同元素即群$G$的不同特征，在$L^2(G)$定义的内积意义下是正交的。

我们假设$\chi_1,\chi_2\in \widehat{G}$是两个不同的群特征，即至少存在一个$g \in G$使得$\chi_1(g)\neq \chi_2(g)$。我们现在需要证明$\langle \chi_1,\chi_2\rangle=0$，也就是要说明和$\sum_{x\in G}\chi_1(x)\overline{\chi_2(x)}=0$。这里我们可以借助[[Symmetric Reduction]]的技巧来完成这件事，即我们要把“和是否为零”这个性质转换为“是否存在一个群元素$g$使得$\chi_1(g)\neq \chi_2(g)$”这样的性质。具体来说，对任意$g\in G$都有$$\begin{aligned}\chi_1(g)\langle \chi_1,\chi_2\rangle&=\sum_{x\in G}\chi_1(x+g)\overline{\chi_2(x)}\\&= \sum_{y\in G}\chi_1(y)\overline{\chi_2(y-g)}\\&= \chi_2(g)\langle \chi_1,\chi_2\rangle\end{aligned}$$这就意味着$$(\chi_1(g)-\chi_2(g))\langle \chi_1,\chi_2\rangle=0$$即是否存在一个这样的$g$满足$\chi_1(g)\neq \chi_2(g)$，如果存在，那么一定有$\langle \chi_1,\chi_2\rangle=0$。于是这样就证明了正交性。

> [!引理2.2]
> $G$是有限交换群，$\widehat{G}$为其对偶群，那么$$|G|=|\widehat{G}|$$

* 首先这个结果在循环群$\mathbb{Z}/m\mathbb{Z}$上是成立的。
这种情形是最简单的有限交换群。因为根据群特征的定义，对任意的有限交换群$G$而言，对任意的特征$\chi$,以及$g\in G$，那么由于$\sum_{i=1}^{|G|}g=1_G$于是$1=\chi(\sum_{i=1}^{|G|}g)=\chi(g)^{|G|}$,于是特征的任何一个取值$\chi(g)$实际上是一个$|G|$次的单位根。

而对于$\mathbb{Z}/m\mathbb{Z}$而言，此群有一个特殊的性质：它的生成元只有一个。这样的话，假设$\chi$是此群的一个特征，$r$是此群一个$n$阶元，那么我们可以将其表示为$r=\sum_{i=1}^{n}a$,于是$$\chi(r)=\chi(\sum_{i=1}^{n}a)=\chi(a)^n$$这就表明，在这个循环群当中，特征完全被它在生成元$a$处的值决定。而由上面的分析$\chi(a)$必然是一个$m$次的单位根，这样的单位根一共有$m$个，于是我们就可以构造出此群的全部特征。令$\xi=e^{\frac{2\pi i }{m}}$,于是令$\chi_k(1_m)=\xi^k$,这样一来$$\chi_k(x):=\xi^{kx}=e^{\frac{2\pi i kx}{m}},k=0,\cdots ,m-1$$而且我们还发现，对偶群$\widehat{\mathbb{Z}/m\mathbb{Z}}$也是一个生成元为$\chi_0(x)=\xi^x$的$m$阶循环群，也就是说$$\mathbb{Z}/m\mathbb{Z}\simeq\widehat{\mathbb{Z}/m\mathbb{Z}}$$
* 接下来我们想到有限交换群的结构定理$$G\simeq \mathbb{Z}/n_1\mathbb{Z}\times \cdots \times \mathbb{Z}/n_{s}\mathbb{Z}$$如果我们可以把循环群上的性质通过结构定理推广到任意有限交换群上，从而得到$$\begin{aligned}\widehat{G}&\simeq \widehat{\mathbb{Z}/n_1\mathbb{Z}}\times \cdots \times \widehat{\mathbb{Z}/n_{s}\mathbb{Z}}\\&\simeq \mathbb{Z}/n_1\mathbb{Z}\times \cdots \times \mathbb{Z}/n_{s}\mathbb{Z}\\ & \simeq G\end{aligned}$$那么问题就可以解决了。

而证明这件事的关键在于:

> [!引理2.3]
> 假设$G,H$分别是两个有限交换群，那么群$G\times H$的对偶群满足$$\widehat{G\times H}\simeq \widehat{G}\times \widehat{H}$$

我们的基本想法是，构造$\Psi,\Phi$分别是从左到右以及从右到左的两个群同态，并且满足$\Psi\circ \Phi=\text{id}_{\widehat{G}\times \widehat{H}},\Psi\circ \Phi=\text{id}_{\widehat{G\times H}}$这样就能证明其中一个比如$\Psi$是一个双射(左逆，右逆都存在)，于是便得到了一个同构映射。
1. $\Psi:\widehat{G\times H}\to \widehat{G}\times \widehat{H}$的定义为对任意$\chi\in \widehat{G\times H},$$$\Psi(\chi):=(\chi_G,\chi_H)$$其中$\chi_G(g):=\chi(g,1_H),\chi_H(h):=\chi(1_G,h)$，那么显然有$\chi_G\in \widehat{G},\chi_H\in \widehat{H}$。并且可以验证这是一个群同态。
2. $\Phi:\widehat{G}\times \widehat{H}\to \widehat{G\times H}$的定义为，对任意的$\chi_1\in \widehat{G},\chi_2\in \widehat{H}$定义$$\Phi((\chi_1,\chi_2)):=\chi_1\chi_2$$很容易验证$\chi_1(g)\chi_2(h)$是群$G\times H$的一个特征，并且$\Phi$是一个群同态。
3. 最后我们需要验证$\Psi\circ \Phi=\text{id}_{\widehat{G}\times \widehat{H}},\Psi\circ \Phi=\text{id}_{\widehat{G\times H}}$,这并不困难。
因此我们肯定$$\widehat{G\times H}\simeq \widehat{G}\times \widehat{H}$$
于是结合引理2.3以及引理2.2下面的分析，我们证明了引理2.2，然后再结合引理2.1于是我们证明了命题2.1。

#### 1.2 函数按照单位正交基的展开

> [!函数的傅里叶级数]
> $G$是有限交换群，$L^2(G)$上的函数$f$按照群特征构成的单位正交基进行展开(分解)，可以表示为$$\begin{aligned}f(x)&=\sum_{\chi\in \widehat{G}} \langle f,\chi \rangle\chi(x)\\&= \sum_{g\in G} \langle f,\chi_g\rangle\chi_g(x)\\&= \sum_{g\in G}\widehat{f}(g)\chi_g(x)\end{aligned}$$其中傅里叶系数被定义为$$\widehat{f}(g):=\langle f,\chi_g\rangle=\frac{1}{|G|}\sum_{x\in G}f(x)\overline{\chi_g(x)}$$

* 此处从内积空间的理解当中来看，函数傅里叶级数展开的傅里叶系数，实际上就是函数的"坐标"。例如假设$G=\mathbb{Z}/n\mathbb{Z}$那么，那么$$\mathcal{B}:=\{e^{\frac{2\pi i kx}{n}}:k=0,\cdots ,n-1\}$$就是一组单位正交基，而函数在此基下的向量可以写成$$[f]_{\mathcal{B}}=(\widehat{f}(0),...,\widehat{f}(n-1))$$

#### 1.3 这样的单位正交基有什么优势？

既然已经有一组形如
$$\delta_g(x):=\begin{cases}1&x=g\\0&\text{otherwise}\end{cases}$$
的单位正交基，（不妨称之为）“$\delta-$基”,为何我们还要去考虑群特征组成的基，(不妨称之为)"傅里叶基"? 


***因为傅里叶基反映了群$G$的代数结构，以及许多重要的线性算子在傅里叶基下是对角的，即这些算子的矩阵表示是对角矩阵。***


一些典型的例子:
1. [[利用roots of unity filter求和]]当中我们需要把函数$$\mathbf{1}_{k|n}(n):=\begin{cases}1&k|n \\ 0&\text{otherwise}\end{cases}$$进行傅里叶展开，准确的说是处理以后的函数$$f(\mathbf{n}):=\begin{cases}1&\mathbf{n}=\mathbf{0}\\ 0&\text{ otherwise}\end{cases}$$这个个处理以后的函数是定义在群$\mathbb{Z}/k\mathbb{Z}$上的。那么由于我们已经知道此群的全部特征的形式，所以我们可以轻易展开函数$f$。



### 2. 有限交换群上的傅里叶变换

> [!有限交换群上的傅里叶变换]
> 函数$f\in L^{2}(G\to \mathbb{C})$的傅里叶变换的结果$\mathcal{F}(f)$是空间$L^{2}(\widehat{G}\to \mathbb{C})$中的函数，其被定义为$$\mathcal{F}(f)(\chi):=\langle f,\chi\rangle=\int_{G}f(x)\overline{\chi(x)}\,d\mu(x)$$在$G$是有限交换群的假设下，因为$G\cong \widehat{G}$，我们往往可以参数化对偶群$\widehat{G}$中的元素,把其中元素表示为$\widehat{G}:=\{\chi_{\xi}:\xi\in G\}$,于是我们还可以把傅里叶变换后的结果表示为$$\widehat{f}(\xi):=\mathcal{F}(f)(\chi_{\xi})=\langle f,\chi_{\xi}\rangle=\int_G f(x)\overline{\chi_{\xi}(x)}\,d\mu(x)$$

* 正如前面提到的，在有限群的意义下，此处的积分因为其测度是“计数测度”，实则应该是求和才对，即$$\widehat{f}(\xi):=\langle f,\chi_{\xi}\rangle=\frac{1}{|G|}\sum_{x\in G}f(x)\overline{\chi_{\xi}(x)},\xi\in G$$在此种情况下，傅里叶系数和傅里叶变换的定义是完全一样的。

> [!有限交换群上函数之间的卷积]
> 两个函数$f,g \in L^{2}(G\to \mathbb{C})$之间的卷积被定义为$$f*g(x):=\int_{G}f(x)g(x-y)\,d\mu(y)$$当然在有限群的离散的"计数测度"意义下，可以写成求和$$f*g(x):=\frac{1}{|G|}\sum_{y\in G}f(x)g(x-y)$$

#### 2.1 傅里叶变换的基本性质

1. 卷积定理:$$\widehat{f*g}=\widehat{f}\cdot \widehat{g}$$
2. 傅里叶逆变换:$$\begin{aligned}f(x)&=\int_{G}\widehat{f}(\xi)\chi_{\xi}(x)\,d\mu(\xi)\\&= \frac{1}{|G|}\sum_{\xi\in G}\widehat{f}(\xi)\chi_{\xi}(x)\end{aligned}$$这实际上就是把函数按照单位正交基$\{\chi_{\xi}(x):\xi \in G\}$进行展开，或者说依照函数在单位正交基下的"坐标"$\widehat{f}(\xi)$的信息重构$f$。
3. Parseval恒等式:$$||f||_{L^2(G)}=||\widehat{f}||_{L^2(G)}$$
4. 酉算子：
如果我们考虑算子$\mathcal{F}:f\mapsto \widehat{f}$,那么这是一个$L^{2}(G)$上的酉算子。因为$\mathcal{F}$是一个双射，因为任意一个函数$g$它的取值就可以构成一个"坐标"，然后我们可以依照单位正交基由此生成一个$L^2(G)$上的函数$f$,从而$$\langle f,\chi_{\xi}\rangle=g(\xi)$$同时又由于Parseval恒等式，任意两个函数$f_1,f_2\in L^2(G)$的内积可以用极化恒等式来表示$$\langle f_1,f_2\rangle=\frac{1}{4}\left(||f_1+f_2||_{L^2}-||f_1-f_2||_{L^2}\right) $$从而因为$\mathcal{F}(f_1+f_2),\mathcal{F}(f_1-f_2)$二者的范数不会改变，从而使得$$\langle \mathcal{F}(f_1),\mathcal{F}(f_2)\rangle= \langle f_1,f_2\rangle$$综上所述，$\mathcal{F}$是一个酉算子，也就是Hilbert空间的一个自同构。

5. 平移不变性：如果我们定义$T_af(x):=f(x-a)$,此处$-a$就是有限群交换群$G$的元素$a$的逆元。那么这种平移后的函数的傅里叶变换为$$\widehat{T_a(f)}(\xi)=\overline{\chi_{\xi}(a)}\widehat{f}(\xi)$$