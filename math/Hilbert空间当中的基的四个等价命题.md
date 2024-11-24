---
tags:
  - math
  - 泛函分析
---

> [!四个等价命题]
> 下列关于一组正交向量是Hilbert空间当中的命题等价:
> 假设$\mathcal{H}$是一个Hilbert空间，并且$\{u_n\}$是空间当中的一组正交向量组，那么以下关于单位正交基的性质是等价的:
> 1. 任意$v\in \mathcal{H}$都有，$S_N(v)=\sum_{|k|\leq N}a_ku_k$依范数(由内积导出的)收敛到元素$v$当$N\to\infty$,其中$a_k=\braket{v,u_k}$
> 2. 成立Parseval不等式，即$||v||^2_{\mathcal{H}}=\sum_{k}|a_k|^2,a_k=\langle v,u_k\rangle$
> 3. $\{u_n\}$当中的元素通过有限线性组合在Hilbert空间$\mathcal{H}$中是稠密的  
> 4. 对于每个非零的元素$v\in \mathcal{H}$,都存在一个单位正交基当中的元素$u_n$使得$\braket{u_n,v}\neq0$。或者换句话说，如果一个$v\in \mathcal{H}$,它与一组正交向量的每个元素都正交，我们可以断定此元素只能是0(几乎处处的意义下)。

### 1. 证明他们的等价性
#### 1.1 1推2
首先是一个垂直关系(来自于定义)$v-S_N(v)\perp S_N(v)$,于是由勾股定理：$$||v||^2=||v-S_N(v)||^2+||S_N(v)||^2$$从而由1的收敛关系，两边取极限则$$||v||=\lim_{N\to\infty}||S_N(v)||^2=\lim_{N\to\infty}\sum_{|k|\leq N}|a_k|^2$$
#### 1.2 从2推出3:
对于任意的$\varepsilon>0$都存在，以及任意的$v\in \mathcal{H}$,因为部分和依照范数收敛到此元素，因此存在 $N_{\varepsilon}$使得$S_{N_{\varepsilon}}=\sum_{|n|\leq N_{\varepsilon}}a_nu_n$，并且$||v-S_{N_{\varepsilon}}||<\varepsilon$。而此部分和是由基有限生成的。

#### 1.3 从3推出4

假设对于非零的元素$v$，任意的n都有$\braket{u_n,v}=0$那么，由于稠密性对于任意的$\varepsilon>0$一定得存在一个$v_{\varepsilon}\in\text{span}(u_n)$使得:$$\braket{v_{\varepsilon}-v,v_{\varepsilon}-v}<\varepsilon$$然后又由于假设，$\braket{v_{\varepsilon},v}=0$于是展开左边不等式变成了$$||v||\leq||v_{\varepsilon}||^2+||v||^2<\varepsilon$$然而这与$v\neq0$矛盾，于是得以证明

#### 1.4 从4回到1

现在我们需要证明$S_N(v)=\sum_{|k|\leq N}a_ku_k$依照范数收敛到$v$。

> [!大致思路]
> 我们发现如果要证明两个元素$a,b \in \mathcal{H}$相等,那么只要证明它与任意单位正交基都是正交的，即$$\braket{a-b,u_k}=0,\forall k \implies a=b$$我们把它改写为更为分析的形式，方便用分析的手段来证明:即对于任意$\varepsilon>0$都有：$$|\braket{a-b,u_k}|<\varepsilon$$
> 于是因为$\mathcal{H}$是完备的空间，而$||S_N(v)||$是单调有界的序列，因此$S_N(v)$是存在一个极限的假设$w\in \mathcal{H}$是其依范数收敛的结果，那么我们实际上只需要证明$$|\braket{w,u_k}|<\varepsilon,\forall k,\forall \varepsilon$$

由于$w$的定义，对于任意$\varepsilon$以及$u_k$，我们都可以找到一个$N_{\varepsilon,k}>k$使得，$||w-S_{N_{\varepsilon,k}}||<\varepsilon$于是:$$\begin{aligned}\braket{w,u_k}&=\braket{w-S_{N_{\varepsilon,k}},u_k}+\braket{S_{N_{\varepsilon,k}},u_k}\\&=\braket{w-S_{N_{\varepsilon,k}},u_k}+a_k\end{aligned}$$所以$$\begin{aligned}|\braket{w,u_k}-a_k|&=|\braket{w-S_{N_{\varepsilon,k}},u_k}|\\&\leq||w-S_{N_{\varepsilon,k}}||\cdot||u_k||\\&<\varepsilon\end{aligned}$$于是便完成了证明.

### 2. 对这些等价命题的应用

#### 2.1 $L^2(\mathbb{R}^d\times \mathbb{R}^d)$的标准正交基

> [!命题1]
> 假设$\{\varphi_k\}_{k=1}^{\infty}$是Hilbert空间$L^2(\mathbb{R}^d)$的一组标准正交基，那么$\{\varphi_{i,j}\}_{1\leq i,j<\infty}$是$L^2(\mathbb{R}^d\times \mathbb{R}^d)$的一组标准正交基，其中$$\varphi_{i,j}(x,y)=\varphi_i(x)\varphi_j(y)$$

事实上这种构造方法不仅仅是用着构造乘积空间的标准正交基上，比如[[关于一个含参数积分极限的两个策略的方法]]当中我们已知$C([a,b])$当中的稠密Banach子代数的构造方法，然后我们需要考虑$C([a,b]\times [c,d])$的稠密子代数

---

首先很自然要验证其单位正交性。

* **单位正交性**:
$$\begin{aligned}\langle\varphi_{i_1,j_1},\varphi_{i_2,j_2}\rangle_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}&=\int_{\mathbb{R}^d\times\mathbb{R}^d}\varphi_{i_1,j_1}\overline{\varphi_{i_2,j_2}}\,dx\,dy\\&= \int_{\mathbb{R}^d\times\mathbb{R}^d}\varphi_{i_1}(x)\varphi_{j_1}(y)\overline{\varphi_{i_2}(x)\varphi_{j_2}(y)}\,dx\,dy\\&=\int_{\mathbb{R}^d}\varphi_{j_1}(y)\overline{\varphi_{j_2}(y)}\left(\int_{\mathbb{R}^d} \varphi_{i_1}(x)\overline{\varphi_{i_2}(x)}\,dx\right)\,dy\\&=\langle\varphi_{i_1}, \varphi_{i_2}\rangle_{L^2(\mathbb{R}^d)}\langle\varphi_{j_1}, \varphi_{j_2}\rangle_{L^2(\mathbb{R}^d)} \end{aligned}$$
其中第三行我们使用Fubini-Tonelli定理对积分进行了换序,参考[[Fubini-Tonelli定理的例子与反例]]当中的技巧：

> [!使用Fubini-Tonelli定理的技巧]
> 我们首先使用Tonelli定理对函数的绝对值进行交换，一切顺利的话，我们可以借此证明要考虑的函数是绝对可积的，于是我们就可以大胆使用Fubini定理了。

首先对$|\varphi_{i_1,j_1}\overline{\varphi_{i_2,j_2}}|$使用Tonelli定理进行交换次序,然后使用Cauchy-Schwarz不等式，确定上界$$\begin{aligned}\int_{\mathbb{R}^d\times\mathbb{R}^d}|\varphi_{i_1,j_1}\overline{\varphi_{i_2,j_2}}|\,dx\,dy&=\langle|\varphi_{i_1}|,|\overline{\varphi_{i_2}}|\rangle_{L^2(\mathbb{R}^d)}\langle|\varphi_{j_1}|,|\overline{\varphi_{j_2}}|\rangle_{L^2(\mathbb{R}^d)}\\&\leq ||\varphi_{i_1}||_{L^2(\mathbb{R}^d)}||\varphi_{i_2}||_{L^2(\mathbb{R}^d)}||\varphi_{j_1}||_{L^2(\mathbb{R}^d)}||\varphi_{j_2}||_{L^2(\mathbb{R}^d)}\\&=1\end{aligned}$$
这样我们就确定了被积函数是绝对可积的，于是我们使用Fubini定理也就得到了上面推理的结果。

于是根据$$\langle\varphi_{i_1,j_1},\varphi_{i_2,j_2}\rangle_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}=\langle\varphi_{i_1}, \varphi_{i_2}\rangle_{L^2(\mathbb{R}^d)}\langle\varphi_{j_1}, \varphi_{j_2}\rangle_{L^2(\mathbb{R}^d)} $$
我们知道，当$i_1=i_2,j_1=j_2$的时候，内积为1，否则内积为0，因此这组向量是单位正交的。

* **形成一个基：**
这里我们选用Hilbert空间的基的四个等价命题当中的第四个，也就是说我们要证明：

> [!成为基的条件]
> 如果存在一个$F\in L^2(\mathbb{R}^d\times \mathbb{R}^d)$使得对所有的$\varphi_{i,j}$都有$$\langle F,\varphi_{i,j}\rangle_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}=0$$
> 那么必然有$F(x,y)=0$对几乎所有点成立.

我们的想法是这样的，假设存在这样的$F$,于是同样利用Fubini定理$$\langle F,\varphi_{i,j}\rangle_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}=\int_{\mathbb{R}^d}\left(\int_{\mathbb{R}^d}F(x,y)\overline{\varphi_i(x)}\,dx\right)\overline{\varphi_{j}(y)}\,dy$$
于是如果我们令$F_i(y):=\int_{\mathbb{R}^d}F(x,y)\overline{\varphi_i(x)}\,dx$,那么内积还可以表示为$$\langle F,\varphi_{i,j}\rangle_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}=\langle F_i,\varphi_{j}\rangle_{L^2(\mathbb{R}^d)}$$
如此一来，对于每一个固定的$F_i\in L^2(\mathbb{R}^d)$,$F_i$与$L^2(\mathbb{R}^d)$当中的全体单位正交基向量正交，于是$F_i(y) = 0$几乎处处成立。这意味着，对于几乎所有固定的$y=y_0$,函数$f(x)=F(x,y_0)$，都有$\langle f,\varphi_{i}\rangle_{L^2(\mathbb{R}^d)}=0$，同样因为单位正交基的缘故，我们知道$f(x)=0$对几乎所有$x$成立。综上所述，我们得到了对于几乎所有$(x,y)$都有$F(x,y)=0$。

不过这里还有一个问题，那就是我们一开始假设$F_i\in L^2(\mathbb{R}^d)$，但是这件事我们还没有验证。

> [!引理1]
> $$||F_j||_{ L^2(\mathbb{R}^d)}\leq ||F||_{L^2(\mathbb{R}^d\times \mathbb{R}^d)}<+\infty$$

这是因为首先我们考察利用Cacuhy-Schwarz不等式考察$$\begin{aligned}|F_j(y)|^2&=\left|\int_{\mathbb{R}^d}F(x,y)\overline{\varphi_i(x)}\,dx\right|^2\\&\leq \left(\int_{\mathbb{R}^d}|F(x,y)|^2\,dx\right)\left(\int_{\mathbb{R}^d}|\varphi_j(x)|^2\,dx\right)\\&=\int_{\mathbb{R}^d}|F(x,y)|^2\,dx\end{aligned}$$
然后考虑其范数的上界，下面的交换次序是因为$F\in L^2(\mathbb{R}^d\times \mathbb{R}^d)$结合Tonelli定理,
$$\begin{aligned}\left\| F_j \right\|^2_{L^2(\mathbb{R}^d)}
&= \int_{\mathbb{R}^d} \left| F_j(y) \right|^2 \, dy
\\&\leq \int_{\mathbb{R}^d} \left( \int_{\mathbb{R}^d} \left| F(x,y) \right|^2 \, dx \right) dy
\\&= \int_{\mathbb{R}^d \times \mathbb{R}^d} \left| F(x,y) \right|^2 \, dx \, dy
\\&= \left\| F \right\|^2_{L^2(\mathbb{R}^d \times \mathbb{R}^d)}\end{aligned}
$$







