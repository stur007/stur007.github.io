---
layout: default
title: "Thoughts on group representation"
date: 2025-10-04
categories: [group theory]
tags: [group theory]
---

Thesedays I'm learning about the (finite) group theory, and I'm going to record my studying notes here, and update them from time to time.

# Group representation
## 1. Linear space and linear transformation
When we first encounter the matrices, we usually put them naturally in the Euclidean space $\mathbb {R}^n$, and the elements of the vectors are the coordinates in the Cartesian coordinate system. However, when we broaden our horizon to the linear space where the bases can be any arbitrary set, we can transform our knowledge into a more general setting.

A vector in a linear space $V$ defined over a number regime $K$ can be viewed as:

$$
X = (e_1, ... , e_n)
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
$$

And the transformation of the vector $X$ by a matrix $A$ can be viewed as either the transformation of the bases(passive view) or the vectors(active view):

Consider a isomorphic mapping $\mathbb A: V \to  V$, which means $X \to AX$. We mapping the coordiantes in the old bases $(e_1, ... , e_n)$ to the new bases $(e_1^\prime, ... , e_n^\prime)$, then we have:

$$
AX = (e_1, ... , e_n)A
\begin{pmatrix} 
x_1 \\
 \vdots \\
  x_n 
\end{pmatrix}
= (e_1^\prime, ... , e_n^\prime)
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
= 
(e_1, ... , e_n)
\begin{pmatrix} 
x_1^{\prime} \\
 \vdots \\
  x_n^{\prime} 
\end{pmatrix}
$$

And the two different bases are related by the matrix $A$ (passive view):

$$
(e_1, ... , e_n)A = (e_1^\prime, ... , e_n^\prime)
$$

the two different coordinates are also related by the matrix $A$ (active view):
$$
\begin{pmatrix}
x_1^{\prime} \\
 \vdots \\
  x_n^{\prime}
\end{pmatrix}
= A
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
$$

- Example: the rotation in $\mathbb{R}^2$.

Let's consider the rotation in z axis in $\mathbb{R}^2$. A vector in $\mathbb{R}^2$ can be expressed as:

$$
X = (e_1, e_2)
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
$$

If we rotate the bases (a isophormic mapping from $\mathbb{R}^2$ to itself) by an angle $\theta$ in the counter-clockwise direction, how can we get the coordiantes of the vector in the new bases?

We can express the old bases in terms of the new bases:

$$
e_1^\prime = \cos \theta e_1  +  \sin \theta e_2 \\
e_2^\prime = -\sin \theta e_1 + \cos \theta e_2
$$

i.e.
$$
(e_1^\prime, e_2^\prime) = (e_1, e_2)
\begin{pmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta  
\end{pmatrix}
$$

So in the passive view, this mapping is:
$$
AX = (e_1, e_2)
\begin{pmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{pmatrix}
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
= (e_1^\prime, e_2^\prime)
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
$$

And in the active view, the coordinates in the new bases are:
$$
AX =
 (e_1, e_2)
\begin{pmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{pmatrix}
\begin{pmatrix}
x_1 \\
x_2
\end{pmatrix}
=
(e_1, e_2)
\begin{pmatrix}
x_1^{\prime} \\
x_2^{\prime}
\end{pmatrix}
$$

---

After understanding the linear space and linear transformation in the Euclidean space, we can forge ahead to the function space, where the bases are functions.

The first porblem we encounter is how to express the transfomation of the functions. The functions are mappings from the coordiates to the values, so we can only focus on the transformation of the coordinates. Say a transformation $\vec r \to A \vec r$, the function still wants to give the same value when $\vec r$ take the same value, so the function should change in the inverse way to keep the value unchanged. i.e. $f(\vec r) \to f(A^{-1} \vec r)$.

- Example: the rotation in function space.
  
    Let's consider the $D_3$ group $\{e, d, f, a, b, c\}$ and the function bases $\Psi_1 = x^2, \Psi_2 = y^2 , \Psi_3 = z^2, \Psi_4 = xy, \Psi_5 = xz, \Psi_6 = yz$. Take the group element $d$ for example. By definition, the element $d$ means rotate the coordinates in the counter-clockwise direction by $120^\circ$ in z axis. Apprently it is more convenient to express this action in the passive view, but calculate in the active view. The rotation gives the relationship between the old bases and the new bases:

    $$
    (e_1^\prime, e_2^\prime)=
    (e_1, e_2)
    \begin{pmatrix}
    \cos \theta & -\sin \theta \\
    \sin \theta & \cos \theta
    \end{pmatrix}
    =
    (e_1, e_2)
    \begin{pmatrix}
    -\frac{1}{2} & -\frac{\sqrt{3}}{2} \\
    \frac{\sqrt{3}}{2} & -\frac{1}{2}
    \end{pmatrix}
    $$

    For function $\Psi_1$, it still wants to give the same value at the same point, which means the mapping should be:
    $$
    \Psi_1^\prime(\vec r^\prime) = \Psi_1(A^{-1}\vec r^\prime) 
    $$

    > To reduce the reduntancy, we will use $\Psi_1$ to denote $\Psi_1^\prime$, which seems to be crazy for mathenaticians, but if we consider the symbol of function as the symbol of mapping, it is ostensible, and we can always distinguish the two functions by their arguments, just like what we always do in physics.

    By definition, we know the transformation for d is the inverse for f, so we have:
    $$
    \Psi_1(\vec r^\prime) = f\Psi_1(\vec r) = \Psi_1(f^{-1} \vec r^\prime ) = \Psi_1(d \vec r^\prime ) = (-\frac{1}{2}x^\prime - \frac{\sqrt{3}}{2}y^\prime)^2 =
    \\ \frac{1}{4}x^{\prime 2} + \frac{3}{4}y^{\prime 2} + \frac{\sqrt{3}}{2}x^\prime y^\prime= \frac{1}{4}\Psi_1 + \frac{3}{4}\Psi_2 + \frac{\sqrt{3}}{2}\Psi_4
    $$

    And that's all for this first function. Reproducing the process for the other five functions, we can get the matrix representation for the group element f in this function space:

    $$
    A(f) =
    \begin{pmatrix}
    \frac{1}{4} & \frac{3}{4} & 0 & \frac{\sqrt{3}}{2} & 0 & 0 \\
    \frac{3}{4} & \frac{1}{4} & 0 & -\frac{\sqrt{3}}{2} & 0 & 0 \\
    0 & 0 & 1 & 0 & 0 & 0 \\
    \frac{-\sqrt{3}}{4} & \frac{\sqrt{3}}{4} & 0 & -\frac{1}{2} & 0 & 0 \\
    0 & 0 & 0 & 0 & -\frac{1}{2} & -\frac{\sqrt{3}}{2} \\
    0 & 0 & 0 & 0 & \frac{\sqrt{3}}{2} & -\frac{1}{2}
    \end{pmatrix}
    $$

## 2. Equivalence representation, irreducible representation and unitary representation 

### 2.1 Brief recap for linear algebra

- Similar matrices
  
  Two $n \times n$ matrices $A$ and $B$ are similar if there is an invertible matrix $P$ such that:
  $$
  B = P^{-1}AP
  $$

  The major property for similar matrices:

  $$
  tr(A) = tr(B) \\
  det(A) = det(B) \\
  $$
  
  And they have the same characteristic polynomial, eigenvalues and eigenvectors.

- Diagonalizable matrix
  
    A square matrix $A$ is diagonalizable if it is similar to a diagonal matrix, i.e. there is an invertible matrix $P$ such that:
    $$
    D = P^{-1}AP
    $$
    
    where $D$ is a diagonal matrix.

- Orthogonal matrix
  
    A square matrix $P$ is orthogonal if its transpose is equal to its inverse, i.e.
    $$
    P^T = P^{-1}
    $$

> Important Theorem: Real symmetric matrices are always diagonalizable by orthogonal matrices. However, the orthogonal matrices are not always diagonalizable in real number regime. *TODO: add a concise proof here.*

All we need to do is to broad these concepts into complex number regime, and we can easily use them in group representation.

### 2.2 Equivalence representation

Two representations $A(g)$ and $B(g)$ of a group $G$ are equivalent if there is an invertible matrix $S$ such that:

$$
A(g) = S^{-1}B(g)S, \forall g \in G
$$

which means, the two representations are **the same representation in different bases.** Let's explain this in detail.

Consider a linear space $V$ with the bases $(e_1, ... , e_n)$, and a representation $B(g)$ of a group $G$ in this space. For any vector $X \in V$, we have:

$$
BX = (e_1, ... , e_n)B(g)
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
$$

Note that we can also express the vector $X$ in another set of bases $(e_1^\prime, ... , e_n^\prime)$, where the two sets of bases are related by an invertible matrix $S$:

$$
(e_1, ... , e_n)S = (e_1^\prime, ... , e_n^\prime)\\
\begin{pmatrix}
x_1^\prime \\
\vdots \\
x_n^\prime
\end{pmatrix}
= S^{-1}
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
$$

Then we can express the transformation of the vector $X$ in the new bases:
$$
X = (e_1, ..., e_n)
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
=
(e_1, ..., e_n)SS^{-1}
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
= 
(e_1^\prime, ..., e_n^\prime)
\begin{pmatrix}
x_1^\prime \\
\vdots \\
x_n^\prime
\end{pmatrix}
$$

So the transformation of the vector $X$ in the new bases is:
$$
AX = (e_1^\prime, ... , e_n^\prime)A(g)
\begin{pmatrix}
x_1^\prime \\
\vdots \\
x_n^\prime
\end{pmatrix}
= 
(e_1, ... , e_n)S A(g) S^{-1}
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
=
(e_1, ... , e_n)B(g)
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}
= BX
$$


So now we know for sure that the two representations $A(g)$ and $B(g)$ are equivalent!

### 2.3 Irreducible representation

A representation $A(g)$ of a group $G$ is called irreducible if there are no nontrivial subspaces $W \subset V$ such that $A(g)W \subset W$ for all $g \in G$. In other words, the only $G$-invariant subspaces are $\{0\}$ and $V$ itself.

The concept of reducible representation is just the opposite of irreducible representation: A representation $A(g)$ is reducible if there exists a nontrivial subspace $W \subset V$ such that $A(g)W \subset W$ for all $g \in G$.

And another important concept is completely reducible representation: A representation $A(g)$ is completely reducible if it can be decomposed into a direct sum of irreducible representations.

### 2.4 Unitary representation

First we should know the concept of inner product in a linear space. An inner product on a complex vector space $V$ is a function $( \cdot , \cdot ) : V \times V \to \mathbb{C}$ that satisfies the following properties for all $u, v, w \in V$ and all scalars $c \in \mathbb{C}$:

1. Conjugate symmetry: $(u, v) = (v, u)^*$
2. Linearity in the first argument: $(cu + v, w) = c(u, w) + (v, w)$
3. Positive-definiteness: $(v, v) > 0$ if $v \neq 0$, and $(v, v) = 0$ if and only if $v = 0$.
4. Sesquilinearity: $(u, cv + w) = \overline{c}(u, v) + (u, w)$

> That's the definition of inner product in mathematics. In physics, we usually use the bra-ket notation to express the inner product, i.e. $\langle u | v \rangle$, and we take the conjugate of the first argument, so the linearity is in the second argument and the sesquilinearity is in the first argument.

A representation $A(g)$ of a group $G$ on a complex inner product space $V$ is called unitary if for all $g \in G$, the matrix $A(g)$ satisfies:
$$A(g)^\dagger A(g) = A(g) A(g)^\dagger = I$$
where $A(g)^\dagger$ is the conjugate transpose of $A(g)$, and $I$ is the identity matrix.

> This definition choose to keep the inner product unchanged under the transformation of the group elements, i.e. for any $u, v \in V$ and any $g \in G$, we have:
>
> $$
> (A(g)u, A(g)v) = (u, v)
> $$

### 2.5 Key theorems in group representation

- First we can prove that any representation of a finite group is equivalent to a unitary representation.

  > Proof: Consider a representation $A(g)$ of a finite group $G$ on a complex inner product space $V$. We can define a new inner product on $V$ by averaging the original inner product over the group elements:
  >
  >$$
  >(u, v)^\prime = \frac{1}{|G|} \sum_{g \in G} (A(g)u, A(g)v)
  >$$
  >
  > where $|G|$ is the order of the group $G$. This new inner product is invariant under the action of the group, i.e. for any $h \in G$, we have:
  >
  >$$
  >  (A(h)u, A(h)v)^\prime = (u, v)^\prime
  >$$
  >
  > Now, we can choose an orthonormal basis for $V$ with respect to this new inner product $(f_1, ..., f_n)$, i.e., 
  >
  > $$
  > X = 
  > (e_1, ..., e_n)
  > \begin{pmatrix}
  > x_1 \\
  > \vdots \\
  > x_n
  > \end{pmatrix}
  > =
  > (f_1, ..., f_n)
  > \begin{pmatrix} 
  > x_1^\prime \\
  > \vdots \\
  > x_n^\prime
  > \end{pmatrix}
  > $$
  >
  > where the two sets of bases are related by an invertible matrix $S$:
  >
  > $$
  > (e_1, ..., e_n)S = (f_1, ..., f_n) \\
  > \begin{pmatrix}
  > x_1^\prime \\
  > \vdots \\
  > x_n^\prime
  > \end{pmatrix}
  > = S^{-1}
  > \begin{pmatrix}
  > x_1 \\
  > \vdots \\
  > x_n
  > \end{pmatrix}
  > $$
  >
  > Note that:
  >
  > $$
  > (Sx, Sy)^\prime = (x_1^{\prime *} , ... , x_n^{\prime *})S^\dagger S
  > \begin{pmatrix}
  > y_1^\prime \\
  > \vdots \\
  > y_n^\prime
  > \end{pmatrix}
  > $$
  >
  > Recall the relationship between the two coordinates, and we have:
  >
  > $$
  > (Sx, Sy)^\prime = (x_1^* , ... , x_n^*)(S^{-1})^\dagger S^\dagger S S^{-1}
  > \begin{pmatrix}
  > y_1^\prime \\
  > \vdots \\
  > y_n^\prime
  > \end{pmatrix}
  > =(x, y)
  > $$
  >
  > If we consider the equivalence representation $B(g) = S^{-1}A(g)S$, then we have:
  >
  >$$
  >(Bx, By) = (S^{-1}A(g)Sx, S^{-1}A(g)Sy) = (A(g)Sx, A(g)Sy)^\prime = (Sx, Sy)^\prime = (x, y)
  >$$
  > which means the representation $B(g)$ is unitary. So we have proved that any representation of a finite group is equivalent to a unitary representation.

- Second, any unitary representation is completely reducible.
  > Proof: Consider a unitary representation $A(g)$ of a group $G$ on a complex inner product space $V$. Let $W$ be a $G$-invariant subspace of $V$, i.e. $A(g)W \subset W$ for all $g \in G$. We want to show that the orthogonal complement of $W$, denoted by $W^\perp$, is also $G$-invariant.
  >
  > For any $u \in W$ and any $v \in W^\perp$, we have:
  >
  >$$
  >(A(g)v, u) = (v, A(g)^\dagger u) = (v, A(g^{-1})u) = 0
  >$$
  >
  > since $A(g^{-1})u \in W$ and $v \in W^\perp$. This shows that $A(g)v \in W^\perp$ for all $g \in G$, so $W^\perp$ is also $G$-invariant.
  >
  > Now, we can decompose the space $V$ into the direct sum of the invariant subspaces $W$ and $W^\perp$. By repeating this process on each invariant subspace, we can eventually decompose the entire space $V$ into a direct sum of irreducible representations. Thus, any unitary representation is completely reducible.

- Finally, we can prove that any representation of a finite group is completely reducible.
  > Proof: Just combine the two theorems above. 

## 3. The theory of group representation

### 3.1 The group space and algebra
Given a group $G$ and a number regime $K$, an element of the group algebra can be written as:
$$
x = \sum_{g_\alpha \in G} x_\alpha g_\alpha
$$
where $x_\alpha \in K$ are the coefficients. The group algebra $R_G$ is the vector space over $K$ spanned by the elements of $G$, with multiplication defined by:

$$
xy = \left( \sum_{g_\alpha \in G} x_\alpha g_\alpha \right) \left( \sum_{g_\beta \in G} y_\beta g_\beta \right) = \sum_{g_\alpha,g_\beta \in G} x_\alpha y_\beta (g_\alpha g_\beta)
$$

where we use the group operation in $G$ to combine the group elements.

> According to the definition above, we can get the definition of the group space $V_G$ as the vector space over $K$ spanned by the elements of $G$, i.e. the elements of $V_G$ are the same as those of $R_G$, but we only consider the vector space structure, ignoring the multiplication.

### 3.2 The canonical representation
The canonical representation of a group $G$ on its group algebra $R_G$ is defined by the left multiplication of the group elements. For each $g \in G$, we define a linear transformation $L: R_G \to R_G$ by:

$$
L(g_i)x = g_i x, \forall x \in R_G
$$

where $L(g_i)$ is called the left regular representation of $G$.

> The right regular representation can be defined in a similar way by the right multiplication of the group elements, i.e. $R(g_i)x = x g_i^{-1}, \forall x \in R_G$.

---

A counterfeit concept of the group algebra is the **group function**. The group function is a function of group elements, i.e. $\Psi = \Psi(g_i)$. 

- If we connect this function with the group vector and the group space, we have:

  $$
    \text{[group vector] } x = \sum_{g_i \in G} \text{ [group function] }x(g_i) \text{ [group element] }g_i
  $$

   And the group space is equivalent to the function space spanned by the group functions.

- If we connect this function with the group representation, we have:

  $$
    A(g_i)x = \sum_{\mu, \nu \in S_p}e_\mu \text{ [group function] }A^p_{\mu\nu}(g_i)x_\nu
  $$
  
  > Note that **we don't have to take the representation space as the group space (or the function space spanned by the group functions).**

### 3.3 Schur's lemma
Schur's lemma is a fundamental result in the theory of group representations. 

- **(Schur's lemma I)** If $A(g)$ and $B(g)$ are two irreducible representations of a group $G$ on complex vector spaces $V$ and $W$, respectively, and if there is a linear transformation $T: V \to W$ such that:

  $$
    T A(g) = B(g) T, \forall g \in G
  $$

  then either $T$ is the zero transformation or $T$ is an isomorphism, which means $A(g)$ and $B(g)$ are equivalence representations of the same group $G$.

- **(Schur's lemma II)** If $A(g)$ is an irreducible representation of a group $G$ on a complex vector space $V$, and if there is a linear transformation $T: V \to V$ such that:

  $$
    T A(g) = A(g) T, \forall g \in G
  $$
  
  then $T$ is a scalar multiple of the identity transformation, i.e. there exists a scalar $\lambda \in \mathbb{C}$ such that $T = \lambda I$.

*TODO:Prove them.*

### 3.4 The great orthogonality theorem
The great orthogonality theorem is a fundamental result in the theory of group representations. It states that the matrix elements of irreducible representations of a finite group are orthogonal with respect to a certain inner product. More precisely,let $|G|$ be the order of group G, and let $A^{p}(g_i)$ and $A^{r}(g_i)$ be two irreducible representations of $G$ of dimensions $S_p$ and $S_r$, respectively. Then the matrix elements of these representations satisfy the following orthogonality relation:

$$
\sum_{g_i \in G} A^{p *}_{\mu\nu}(g_i) A^{r}_{\mu^\prime\nu^\prime}(g_i) = \frac{|G|}{S_p} \delta_{pr} \delta_{\mu\mu^\prime} \delta_{\nu\nu^\prime}
$$

where $A^{p}_{\mu\nu}(g_i)$ is the $(\mu,\nu)$-th matrix element of the representation $A^{p}(g_i)$,  and $\delta_{pr}$ are Kronecker deltas.

*TODO:Prove it.*

### 3.5 The completeness theorem
The completeness theorem states that the matrix elements of irreducible representations of a finite group form a complete set of functions on the group. More precisely, let $A^{p}(g_i)$ be an irreducible representation of $G$ of dimension $S_p$. Then the matrix elements $A^{p}_{\mu\nu}(g_i)$, where $\mu,\nu = 1,\ldots,S_p$, form a complete set of functions on the group $G$.

This means that any function $f: G \to \mathbb{C}$ can be expressed as a linear combination of the matrix elements of the irreducible representations:

$$
f(g) = \sum_{p} \sum_{\mu,\nu} c^{p}_{\mu\nu} A^{p}_{\mu\nu}(g)
$$

where $c^{p}_{\mu\nu} \in \mathbb{C}$ are coefficients that depend on the function $f$ and the representation $A^{p}(g)$.

*TODO:Prove it.*

> TO BE CONTINUED...