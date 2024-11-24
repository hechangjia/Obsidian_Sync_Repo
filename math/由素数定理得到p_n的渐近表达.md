---
tags:
  - math
  - 解析数论
---
### 1.由素数定理(PNT)可以得到关于第n个素数的渐近表达
$$p_n \sim n\log(n)$$
1.  其想法是来自于由素数定理$\pi(x)\sim \frac{x}{\log(x)}$并且利用$\pi(p_n)=n$这个结果然后利用$\sim$的表达在乘积当中的替换，于是: $$p_n
    = \frac{p_n}{\log(p_n)}\log(p_n)\sim \pi(p_n)\log(p_n) =
    n\log(p_n)$$那么我们是需要搞清楚$\log(p_n)$的渐近结果就好了。
2.  $\log(p_n)$的结果是来自于$\log(\pi(x))\sim\log(x)$,这个结果会导致:
$$\log(n) \sim \log(p_n)$$于是$$p_n \sim n\log(p_n)\sim
 n\log(n)$$
3.  $\log(\pi(x))\sim\log(x)$的结果是由PNT直接导出的,因为$$\pi(x)
    = \frac{x}{\log(x)} + o\left(
    \frac{x}{\log(x)}\right)$$两边取对数就能比较轻易得到。
