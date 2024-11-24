---
tags:
  - math
  - 实分析
  - 调和分析
---


> [!Wirtinger inequalities(special cases of Poincare inequality)]
> -   a:如果$f$是周期为$T$的连续周期函数($f(0)=f(T)$),并且分段$C^{1}$,以及$\int_0^Tf(t) d t=0$那么:$$\displaystyle \int_0^T|f(t)|^2 d t \leq \frac{T^2}{4
> \pi^2} \int_0^T\left|f^{\prime}(t)\right|^2 d t$$ 即 $$ ||f||^2 \leq \frac{T^2}{4
> \pi^2}||f^{\prime}||^2$$
> 
> -   b:对于$f\in C[a,b]$函数可微,且$f(a)=f(b)=0$，都有:$$ \int_a^b|f(t)|^2 d t \leq \frac{(b-a)^2}{\pi^2}
> \int_a^b\left|f^{\prime}(t)\right|^2 d t$$即$$||f||^2 \leq \frac{(b-a)^2}{\pi^2} ||f'||^2$$

## 证明思路
-   主要思路:
$$\int_0^T|f(t)|^2 d t
,\int_0^T\left|f^{\prime}(t)\right|^2 d t$$
这样的连续可微函数的积分让我们可以在$L^2(0,T])$当中考虑问题,从而把积分的问题转换为离散的求和问题。

-   **a的证明**：因为函数是连续周期函数，所以可以使用Parseval's identity:$$\frac{1}{T} \int_{0}^{T} |f(x)|^2 dx= \sum_{n \in
\mathbb{Z}} |\hat{f}(n)|^2$$同时知道函数与其导数的傅里叶系数的关系($n \neq 0$):

$$\begin{aligned} \hat{f}(n) & =\frac{1}{T} \int_0^T f(t)
e^{-\frac{2 \pi}{T}i n t} d t \\ &
=\frac{1}{T}\left[f\left(0^{+}\right)-f\left(T^{-}\right)\right]
\frac{T}{2 \pi i n}+\frac{T}{2 \pi i n} \cdot \frac{1}{T}
\int_0^T f^{\prime}(t) e^{-\frac{2 \pi}{T}i n t} d t \\ &
=\frac{T}{2 \pi i n} \hat{f}^{\prime}(n) \end{aligned}$$
注意这里关键有一个条件$\left[ f\left(0^{+}\right)-f\left(T^{-}\right)\right]=0$，否则函数的傅里叶系数和其微分的傅里叶系数不会有上面的关系。所以这就是为什么前面给出了那个条件是必要的。所以$$\int_0^T|f(t)|^2 d t=T
\sum_{|n|>0}|\hat{f}(n)|^2=\frac{T^3}{4 \pi^2}
\sum_{|n|>0}
\frac{\left|\hat{f}^{\prime}(n)\right|^2}{n^2}$$因为$\hat{f}(0) = 0$同样也可以知道$\hat{f}^{\prime}(0) =0$所以进一步，如果对$f^{\prime}$也使用Parseval's identity$\hat{f}(0) = 0$是因为$\hat{f}(0) = \frac{1}{T} \int_{0}^{T}f(x) dx = 0$$$ \frac{T^3}{4 \pi^2} \sum_{|n|>0}
\frac{\left|\hat{f}^{\prime}(n)\right|^2}{n^2} \leq
\frac{T^3}{4 \pi^2}
\sum_{|n|>0}\left|\hat{f}^{\prime}(n)\right|^2\leq\frac{T^3}{4
\pi^2} \cdot \frac{1}{T}
\int_0^T\left|f^{\prime}(t)\right|^2 d t=\frac{T^2}{4
\pi^2}||f^{\prime}||^2$$等式成立的条件是，当且仅当 $\hat{f}^{\prime}(n) = 0,|n|>1$,由于导数的傅里叶系数和原来的傅里叶系数相差只有一个系数，所以$\hat{f}(n)=0,|n|>1$.也就是说，这个函数$\hat{f}(1),\hat{f}(-1)$ 以外，所有其他项的傅里叶系数都是0.

同时注意到,如果$f \in C^{1}(\mathbb{T})$,那么其傅里叶级数是绝对收敛的,因此其傅里叶级数是一致收敛到函数本身的。因此函数可以等价于它的傅里叶展开
那么最后如果上述不等式取等号，函数就可以写成:$$f(t)=\hat{f}(1)e^{\frac{2\pi}{T}it}+\hat{f}(-1)e^{-\frac{2\pi}{T}it}=A\cos\left(\frac{2\pi}{T}t\right) +
B\sin\left(\frac{2\pi}{T}t\right)$$
其中$A,B \in \mathbb{C}$

-   b :
可以把函数拓展成周期函数,在一个周期$[a,2b-a]$内把函数定义为(也就是把做左右的对称，然后上下的对称):

$$F(t)=\left\{\begin{array}{c} f(t), t \in[a, b) \\
-f(2b-t), t \in(b, 2 b-a] \end{array}\right.$$
这样才能保证连接处导数有定义，并且左右导数相同。

由于构造还可以得到这样的结论:

$$ \int_a^{b}|f(t)|^2 d t=\int_{b}^{2b-a} |f(t)|^2 d t$$

其导数也有类似的结论，于是运用a得到的用导数的模来控制函数的模的结论，可以得到:
$$||f||^2 \leq \frac{(b-a)^2}{\pi^2} ||f'||^2$$

等号成立的条件和上面一样，然后用上上面构造的化简，可以得到:

$$f(t)=A \sin \left(\pi \frac{t-a}{b-a}\right)$$

