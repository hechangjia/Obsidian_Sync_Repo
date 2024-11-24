---
tags:
  - math
  - 组合学
  - 中学数学竞赛
---

> [!问题]
> 假设$S$是丢番图方程$i+j+k=17$的正整数解的解集，求和$$\sum_{(i,j,k)\in S}ijk$$

### 1.过滤器这个想法的推广

关于这类丢番图方程的正整数解的数量我们在[[线性丢番图方程非负整数解的个数]]这个问题当中已经搞清楚了，但是这里并非统计解的个数而是用解来计算一个新的求和。不过换个角度来思考，正整数解的个数不也是一个和，即$$\sum_{(i,j,k)\in S}1$$
更确切地说，在那个问题当中，我们找到生成函数
$$F(z) =(1+z+...)(\chi_1(0)+\chi_1(1)z^1+\chi_1(2)z^2+...)(\chi_2(0)+\chi_2(1)z^1+\chi_2(2)z^2+...)$$
其中$\chi_1,\chi_2$是所谓地偶数以及3的倍数的过滤器，最后展开的时候实际上是
$$\begin{aligned}F(z)&=\sum_{n\geq 0}\left(\sum_{x_1+x_2+x_3= n }1\cdot \chi_1(x_2)\chi_2(x_3)\right)z^{n}\\ &= \sum_{n\geq 0}A_nz^n\end{aligned}$$
也就是说，除非$x_2,x_3$同时满足$\chi_1,\chi_2$两个条件即一个是2的倍数，另一个是3的倍数，否则会得到0.

这个想法如果一般化，我们可以总结为

> [!过滤器这个想法的一般化]
> $$\begin{aligned}F(z)&=\prod_{r=1}^{n}(\varphi_r(0)+\varphi_r(1)z+\varphi_r(2)z^2+...)\\ &=\sum_{m\geq 0}\left(\sum_{x_1+...+x_n= m }\prod_{r=1}^{n}\varphi_r(x_r)\right)z^{m}\\ &= \sum_{m\geq 0}A_mz^m \end{aligned}$$
> 如果我们假设$S_m$是丢番图方程$x_1+...+x_n=m$的非负整数解，那么我们还可以把$A_m$表达为$$A_{m}=\sum_{(x_1,...,x_n)\in S_m}\varphi_1(x_1)\cdot \cdot \cdot \varphi_r(x_r)$$

从这个角度上来看，一些常见问题不过是这个想法的特殊情况:
1. **正整数解**：此时$\varphi_r=\chi_{>0}$后者是正实数的判断函数，负责过滤掉所有的0.
2. **加权的线性丢番图方程的非负整数解**：也就是$a_1x_1+...+a_nx_n=m$的非负整数解。这个情况下$\varphi_r =\chi_{\text{mod }a_r =0}$也就说要过滤掉所有不是$a_r$的倍数的情况。
### 2.此问题生成函数的构造

这个问题实际上也可以视为上面提到的想法的特殊情况，即$\varphi_1(i)=i,\varphi_2(j)=j,\varphi_3(k)=k$于是自然知道生成函数是$$\begin{aligned}G(z)&=\left(\sum_{i\geq 0}iz^i\right)\left(\sum_{j\geq 0}jz^j\right)\left(\sum_{k\geq 0}kz^k\right)\\ &=\left(\frac{x}{(1-x)^2}\right)^3 = \frac{x^3}{(1-x)^6}\end{aligned}$$
而这个生成函数展开的第17项系数就是$\sum_{(i,j,k)\in S}ijk$的结果,根据[[线性丢番图方程非负整数解的个数]]第一部分提到的公式$$\frac{1}{(1-z)^{m}} = \sum_{n\geq 0} \binom{n+m-1}{m-1} z^n$$
也就是$\binom{19}{5}$.
