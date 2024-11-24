---
tags:
  - math
  - 复分析
---
我们需要给出$\Gamma(z+1)-1$在$z =0$处的渐进展开。

### 1.从整体上分析
$\Gamma(z)$是定义在整个复平面上的亚纯函数，极点是实轴上的非正整数点，例如$0,-1,-2,....$,在$\text{Re}(z)>0$的右半平面上函数全纯(详细可以参考[[证明Gamma函数在右半平面上全纯]])并且有积分表示:
$$\Gamma(z):=\int_{0}^{\infty}
t^{z-1}e^{-t}dt$$也就是说，我们想要得到此函数在$z =1$处的渐进展开，函数在此点邻域内是解析的，因此不妨直接展开为级数的形式。想要得到级数展开，也就是Taylor展开，我们必须要知道此函数的导数怎么算.

由于此函数在右半平面上，可以视为一个含参数的积分，那么可以交换微分和积分的次序，从而得到导数的公式:

$$\Gamma^{(n)}(z)=\int_{0}^{\infty}\log^{n}(t)t^{z-1}e^{-t}dt$$如此一来，
$$\Gamma(z+1)=\Gamma(1)+\Gamma'(1)z+\frac{\Gamma''(1)}{2!}z^2+O(z^3)$$其中:
1.  $\Gamma(1)=0!=1$
2.  $\Gamma^{'}(1)=\int_{0}^{\infty}\log(t)e^{-t}dt=-\gamma$
3.  $\Gamma^{''}(2)=\int_{0}^{\infty}\log^2(t)e^{-t}dt=\gamma^2+\frac{\pi^2}{6}$

因此渐进展开为:
$$\Gamma(z+1)=1-\gamma
z+\left(\frac{\gamma^2}{2}+\frac{\pi^2}{12}\right)z^2+O(z^3)$$当然，如果是对于$\Gamma(z)$在$z=0$的展开，考虑到这里面包含一个极点，于是有Laurent展开，不过也考虑到和上面的展开的联系，因为$\Gamma(z+1)=z\Gamma(z)$所以:

$$\Gamma(z)=\frac{1}{z}-\gamma
+\left(\frac{\gamma^2}{2}+\frac{\pi^2}{12}\right)z+O(z^2)$$



### 2.从把含参数积分转换为级数的思路出发

同样从函数的积分表示入手，有一个技巧可以把含参数积分转换为级数，也就是把被积分对象进行级数展开，然后交换求和与积分次序。
$$t^{z} = \exp(z\log(t))=\sum_{n\geq 0}
\frac{\log^n(t)}{n!}z^n$$于是

$$\begin{aligned}\Gamma(z+1)&= \int_{0}^{\infty}
t^{z}e^{-t}dt\\&=\int_{0}^{\infty} \left(\sum_{n\geq 0}
\frac{\log^n(t)}{n!}z^n\right)e^{-t}dt \\&=\sum_{n\geq
0}\frac{1}{n!}\left(\int_{0}^{\infty}\log^n(t)e^{-t}dt\right)z^n\\&=\sum_{n\geq
0}\frac{1}{n!}\Gamma^{(n)}(1)z^n
\end{aligned}$$也就是说，通过这种反思我们也可以得到Taylor展开。这种技巧实际上也是我们通过全纯函数的柯西积分公式得到函数泰勒展开的技巧。

