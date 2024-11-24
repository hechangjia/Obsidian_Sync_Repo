---
tags:
  - math
  - 实分析
---

> [!求含参数积分的极限]
> $f \in L^{1}([a,b])$并且$g$是周期为$T$的可测有界周期函数: $$\lim_{n
> \to +\infty}\int_{a}^{b} f(x)g(nx) dx $$ 

### 1.这类逼近的通用做法都是：先控制好n不变，然后得到$\varepsilon$的不等式，然后取极限

假设对于函数 $f$存在一个更简单版本的函数$f_{\varepsilon}$,这个函数在$L^{1}(a,b])$当中可以逼近$f$,即:
$$\forall \varepsilon >0,\exists f_{\varepsilon } \text{ s.t. }
||f-f_{\varepsilon}||<\varepsilon$$并且后者之所以称之为更简单版本，是因为它的极限很好算(当然要存在)，有一个明确的关于$f_{\varepsilon}$的公式:
$$A_n(f_{\varepsilon})=\int_{a}^{b} f_{\varepsilon}(x)g(nx)
dx$$
$$A(f_{\varepsilon})=\lim_{n\to \infty}\int_{a}^{b}
f_{\varepsilon}(x)g(nx) dx$$

(这里特别强调，上面的两个式子至少渐近展开式子要有明确的形式)
那么要求的积分的极限其实形式上和简化版本的是一样的。

翻译成更具体的数学语言，我们要证明的是，如果$$I_n(f)=\int_{a}^{b} f(x)g(nx)
dx$$并且满足:
$$|I_n(f)-A(f)|<\varepsilon ,\forall \varepsilon
>0$$那么一定有:
$$\lim_{n\to \infty} I_{n}(f) = A(f)$$这是因为:

$$\begin{aligned}|I_n(f)-A(f)|&\leq
|I_n(f)-A_{n}(f)|+|A_n(f)-A(f)| \\ &< M\varepsilon +
|A_n(f)-A(f)|\end{aligned}$$其中$M$是函数$g$的上界(所以函数的有界性也是必要的)。两边取上极限，于是:

$$\limsup_{n\to \infty}|I_n(f)-A(f)|<M\varepsilon ,\forall
\varepsilon >0$$于是
$$\limsup_{n\to \infty}|I_n(f)-A(f)| = 0$$于是

$$\lim_{n\to
\infty}I_n(f)=A(f)$$这就是上面那句话,**要求的积分的极限其实形式上和简化版本的是一样的。**

所以最后的问题就归结为，选择哪个可以逼近$f$的函数，并且其在这个问题下的积分是容易计算/渐近的?

### 2. 使用简单函数做逼近
简单函数比连续函数更好算，假设$h(x)$是一个简单函数，那么有下面的计算:

$$\begin{aligned}\int_{a}^{b} h(x)g(nx) dx = \sum_{k} a_k
\int_{x_k}^{x_{k+1}} g(nx)dx &\to \sum_{k} a_k
\left(\frac{(x_{k+1} -x_k)}{T}\int_{0}^{T} g(x) dx \right) \\
&= \left(\sum_{k} a_k (x_{k+1}
-x_k)\right)\left(\frac{1}{T}\int_{0}^{T} g(x) dx \right) \\ &=
\left(\int_{a}^{b} h(x) dx
\right)\left(\frac{1}{T}\int_{0}^{T} g(x) dx \right)
\end{aligned}$$
这里注意到要算一个这种含有参数的周期函数在任意的闭区间上的积分的技巧，如果积分是由很多个小区间组成，小区间内好计算或者好渐进，那么不妨可以转换积分为求和问题。

于是这里我们知道上面需要的那个具体的表达式:

$$A(h) = \left(\int_{a}^{b} h(x) dx
\right)\left(\frac{1}{T}\int_{0}^{T} g(x) dx
\right)$$于是按照上面的分析,一般情形下,$f$的整个含参数积分的极限也有相同的形式:

$$A(f) = \left(\int_{a}^{b} f(x) dx
\right)\left(\frac{1}{T}\int_{0}^{T} g(x) dx \right)$$即:

$$\lim_{n \to +\infty}\int_{a}^{b} f(x)g(nx) dx = A(f)$$

* 以上思路也同样应用于傅里叶系数版本的[[Riemann - Lebesgue lemma的证明]]当中。



