---
layout: default
title: "Mid-Term Review For Group Theory"
date: 2025-10-04
categories: [group theory]
tags: [group theory]
---

# 群的基本概念

## 定义

- 封闭性
- 结合律
- 存在唯一的单位元素
- 存在唯一的逆元

## 重排定理

用一个群中的元素乘以群中的所有元素，相当于对群做一次重排。

> 证明是非常简单的，只需要用到群的定义就行，但是这一定理的使用价值非常高，可以证明很多命题。

## 子群

子群=群+子集（真子集对应于非平庸子群， 非真子集对应于平庸子群）。证明只需封闭性与逆元存在即可，其他性质自动满足。

> 构造（寻找）子群的最简单方式就是循环群，循环群也非常重要，在证明很多关于子群的性质的时候都有用。

## 陪集定理

可以用陪集分割群，结论就是Lagrange定理：子群的阶一定是群阶的因子。

> 例子：
> ![20251102104506](https://raw.githubusercontent.com/stur007/img/main/img/20251102104506.png)
> > 群的阶是群中元素的个数，元素的阶是元素生成的循环群中元素的个数。

## 类

可以通过共轭关系$hgh^{-1}=f$联系在一起的元素($g, f$)同为一个类。

## 类中元素个数的定理

类中元素的个数一定是群阶的因子。

> 证明需要考虑类中元素的生成过程，找到与之对易的元素构成子集，用Lagrange定理即可。这个定理主要在应用层面比较重要，尤其是点群的部分。

## 共轭子群与不变子群

共轭子群是说两个群可以通过一个元素共轭联系起来，不变子群是说子群的共轭子群是自身。

> 比较方便的寻找不变子群的方法是用它的另一个等价定义：先不变，后子群 -> 由几类元素构成的子群。

> 例子：$D_4$群群元分类与不变子群，这一点在学了点群以后就简单了。
> ![20251102105743](https://raw.githubusercontent.com/stur007/img/main/img/20251102105743.png)
> > $D_4$群的非平庸不变子群是：$C_4, C_2, D_2^{(1)}, D_2^{(2)}$.

## 商群

群按照不变子群分割得到的陪集作为元素构成的群，在同态映射的时候特别有用。

## 同构映射

同构是说两个群是同一个群，$G \cong H$。

## 同态映射

将不变子群映射到单位元素，将陪集映射到其他元素。这一点是由**同态核定理**保证的。

## 自同构映射

群到自身的映射，将单位元素映成单位元素，互逆元素映成互逆元素。

## 内自同构映射

这个映射操作是通过群中元素的共轭操作实现的。

## 变换群

其实想想看，这一概念就是群表示理论的初步。定义群变换的空间（群表示中是线性空间），群元操作（群表示中是线性操作），就是变换群。

> $S_G$变换空间是G的群（群空间）。**Cayley**定理给出，群$G$一定是$S_G$的子群，（所以群$G$一定有正则表示）。


## 轨道与不变子集

在群G操作下不变的集合是不变子集，在G操作下等价（可以相互抵达的点）的点是G轨道。

> 结论：G轨道上的点以及他们的任意并是不变子集。

## 迷向子群

注意“子群”是G中元素的概念，这里指的是对于某一元素x，使得这一点保持不变的操作的子群。**这一点在书上的定义并不明确，其实他要表达的意思是，迷向子群$G^x = {\forall h \in G, h \cdot x = x}$。**

> 用迷向子群分割群得到的陪集，会不重不漏地给出x的G轨道上的点。其实这就是**轨道-稳定子定理**，所谓的迷向子群在这一定义下就是稳定子群。可以证明稳定子构成的集合一定是群（封闭性与逆元存在），接着证明这一定理也是显然的，作为复习，下面证明一下：
>
> 不妨 $G = \{g_0 G^x, ..., g_l G^x\}$. 对于同一个$g_i G^x$中的元素，显然得到是相同的点；对于不同$g_i G^x, g_j G^x$ 中的点，如果给出同一个点，说明$g_i x = g_j x$，说明$g_i^{-1}g_j \in G^x$. 由重排定理，$g_i^{-1}g_j G^x = G^x$. $g_i G^x = (g_i^{-1}g_j G^x) = g_j G^x$, 矛盾（给出的不是不同陪集）.

例子：
> ![20251102125338](https://raw.githubusercontent.com/stur007/img/main/img/20251102125338.png)

## 直积

对一个群做直积分解，得到的两个群是等价的，同时都是不变子群。（用直积分解的定义可以证明）

具体而言，$(g_{1\alpha}g_{2\beta})(g_{1\alpha}^\prime g_{2\beta}^\prime )= (g_{1\alpha}g_{1\alpha}^\prime )(g_{2\beta}g_{2\beta}^\prime)$。当然这种带括号的定义是没有什么意思的，补充定义二者之间的乘法（就是直积分解）才是我们关注的重点。

例子：
> ![20251102114338](https://raw.githubusercontent.com/stur007/img/main/img/20251102114338.png)

> 直积分解也不是唯一的，但是可以通过直积分解得到很多直积群的性质。

## 半直积

定义：群$G_2$是群$G_1$的自同构映射群的同态映射，有：

$$
<g_{1\alpha}g_{2\beta}><g_{1\alpha}^\prime g_{2\beta}^\prime >= <g_{1\alpha} \nu_{2\beta}(g_{1\alpha}^\prime)><g_{2\beta}g_{2\beta}^\prime>
$$

> 注意这里的同态映射不要求是满射，如果$G_2$被映射为了$G_1$的自同构群中的单位元素，那么这就是直积。同时这也反映出半直积分解一般不是唯一的。

# 群的表示理论

这一部分的内容比较抽象，一些比较严谨的讨论在[group representation](https://stur007.github.io/group%20theory/2025/10/04/group-representation.html)中。主要的想法是，用一套统一的语言（线性代数）表示群之间的关系，用抽象的变换代替具体的群元（用数字3代表三个苹果）。此外，同构线性代数的性质可以得到群之间的性质，这是我们感兴趣的点。

## 线性空间与线性变换

主要抓住基的选取和向量、变换之间的关系即可。这一部分在上面的链接中有比较好的讨论，直观的理解：

![discussion_page-0001](https://raw.githubusercontent.com/stur007/img/main/img/discussion_page-0001.jpg)

![discussion_page-0002](https://raw.githubusercontent.com/stur007/img/main/img/discussion_page-0002.jpg)

![discussion_page-0003](https://raw.githubusercontent.com/stur007/img/main/img/discussion_page-0003.jpg)

## 线性空间的内积

内积的定义方式有很多种，只要满足内积的要求即可（主要是一个半线性）。但是一般这里常用的内积定义方式是，

$$
(\vec x | \vec y) = \frac 1 n \sum_i^n  x_i^* y_i 
$$

## 线性变换群

复 ($\mathbb C$) 线性空间 ($V$) 上的所有非奇异 ($det A \neq 0$) 线性变换构成一个群 $GL(V, \mathbb C)$. 

## 忠实表示

就是同态映射退化成了同构映射。

## 群的线性表示的关系

群表示的分解：要将一个群的线性表示分解成一系列（不可约）表示的直和（群表示的约化，用矩阵的语言说就是矩阵的同时对角化）。

群表示的等价：可以通过一个相似变换联系起来的表示。

研究群的线性表示，就是找到所有的不等价不可约（酉/幺正）表示。借助线性代数中的结论，这一部分的研究就变得简单了。

### 线性代数知识

- 在有限维复线性空间中，酉（幺正）矩阵 $U^\dagger U = 1$ 和 厄米矩阵 $U = U^\dagger$ 可以酉（幺正）相似对角化；
  > 证明是简单的，可以直接用数学归纳法。
- 矩阵同时对角化的充分条件：两个矩阵可以交换，并且至少有一个可以对角化。
  > 使用不变子空间的性质，这一点也是容易证明的。

在群表示理论中这一结果更加宽泛：
> ![20251102140147](https://raw.githubusercontent.com/stur007/img/main/img/20251102140147.png)

### 群的线性表示的特殊性质

- 群的任意一组表示一定等价于一组酉表示；（Schur 引理的推论）
- 酉表示可约则完全可约；（用酉表示的性质直接证明）

> 结论：任意一组群的线性表示一定等价于一系列不等价不可约酉表示的直和。

## 正则表示

研究正则表示的目的是得到**所有的不等价不可约表示**。正则表示的定义非常简单，将群元作为基生成的的线性空间叫做群空间，群元之间的代数叫做群代数，群元在群空间的表示叫做正则表示，定义在群上的函数叫做群函数。取出一组群函数构成的线性空间叫做群函数空间，这个空间和群空间是同构的。

另外，正则表示还分为左正则表示和右正则表示，其实是一样的。

![20251102172151](https://raw.githubusercontent.com/stur007/img/main/img/20251102172151.png)

> 这一证明在书中也有别的方法，用的是证明完备性定理时候的一个中间性质。

## （不等价不可约）表示（作为群函数的）正交性定理和完备性定理

这是群表示理论中我觉得最神奇的定理，根据这一点可以得到群表示的很多性质。

### 正交性定理

$$
(A^{p}_{\mu\nu}|A^{r}_{\mu^\prime\nu^\prime}) = \frac 1 {S_p} \delta_{pr} \delta_{\mu\mu^\prime} \delta_{\nu\nu^\prime}
$$

### 完备性定理

$$
f(g) = \sum_{p} \sum_{\mu,\nu} c^{p}_{\mu\nu} A^{p}_{\mu\nu}(g)
$$ 

### 有用的推论（Burnside 定理）

$$
n = \sum_{所有不等价不可约表示} d_i(第i个不等价不可约表示的维数)^2
$$

## 特征标理论

不等价不可约表示虽然完全，但是还是太复杂了，特征标就很好的解决了这一问题。

### 正交性定理

$$
(\chi^p|\chi^r) = \delta_{pr}
$$

$$
\frac {n_i}{n}\sum_p (\chi^p)^*(g_i) \chi^p(g_j) = \delta_{ij} 
$$

### 完备性定理

$$
f(K_i) = \sum_p c_p \chi^p(k_i)
$$

例子：
> ![20251102172622](https://raw.githubusercontent.com/stur007/img/main/img/20251102172622.png)
>
> 从中可以看出循环群的巨大威力。

## 总结

对于群来说，最直接、准确的表示就是群的乘法表。但是仅仅就事论事是不可能研究清楚群之间的关系的，所以使用群（在线性空间上）的表示来分析这个群。不等价不可约表示比较复杂（但是信息完善），使用特征标理论得到了群的主要信息（但是信息不完善）。

> 前一个命题的证明：如果同构，那么不可约表示相同；如果不可约表示相同，使用反证法，那么不可能所有的表示都相同（至少有忠实表示），但是不可约表示相同，所以正则表示也相同或者差一个相似变换，那么两个群同构，矛盾！后一个可以举出反例，这是比较明确的($D_4$ <mark>可以做半直积分解</mark> 和 $Q_8$)。

## 附录：定理的证明

![Group Theory Proof of the theorems in Chap 2_page-0001](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0001.jpg)

![Group Theory Proof of the theorems in Chap 2_page-0002](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0002.jpg)

![Group Theory Proof of the theorems in Chap 2_page-0003](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0003.jpg)

![Group Theory Proof of the theorems in Chap 2_page-0004](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0004.jpg)

![Group Theory Proof of the theorems in Chap 2_page-0005](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0005.jpg)

![Group Theory Proof of the theorems in Chap 2_page-0006](https://raw.githubusercontent.com/stur007/img/main/img/Group%20Theory%20Proof%20of%20the%20theorems%20in%20Chap%202_page-0006.jpg)

# 点群和空间群

这一部分的讨论比较简单，参见后面的附页。

![group_theory_cheatsheet_page-0001](https://raw.githubusercontent.com/stur007/img/main/img/group_theory_cheatsheet_page-0001.jpg)

![group_theory_cheatsheet_page-0002](https://raw.githubusercontent.com/stur007/img/main/img/group_theory_cheatsheet_page-0002.jpg)