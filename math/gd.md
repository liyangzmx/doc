# 线性方程组的解
## 解线性方程组的矩阵消元法
左端都是未知量 $x_1,x_2,x_3,x_4,x_5$ 的一次齐次式, 右端是常数, 这样的方程组成为**线性方程组**. 每个未知量前面的数称为系数.

含 n 个未知量的线性方程组成为 **n 元线性方程组**, 它的一般形式是:
$$
\left\{\begin{align*}
    a_{11}x_1+a_{12}+\cdots+a_{1n}x_n&=b_1 \\
    a_{21}x_1+a_{22}+\cdots+a_{2n}x_n&=b_2 \\
    \cdots \\
    a_{n1}x_1+a_{n2}+\cdots+a_{nn}x_n&=b_n \\
\end{align*}\right.
$$
其中 $a_{11},a_{12},\cdots,a_{nn}$ 是系数, $b_{1},b_{2},\cdots,b_{n}$ 是常数项, 常数项一般写在等号右边.

**定义 1** 由 $s\cdot m$ 个数排成 $s$ 行, $m$ 列的一张表称为一个 $s\times m$矩阵, 其中每一个数称为这个矩阵的**一个元素**, 第 $i$ 行与第 $j$ 列交叉位置的元素称为矩阵的 **$(i,j)$ 元**. 元素全为0的矩阵称为**零矩阵**, 简记作: $0$, $s$ 行 $m$ 列的零矩阵可以记作 $0_{s\times m}$

矩阵的三种初等行变换:
1. 把一行的倍数加到另一行上
2. 互换两行的位置
3. 用一个非零数乘某一行

阶梯形矩阵的特点:
1. 元素全为0的行(称为**零行**)在下方(如果有零行的话)
2. 元素不全为0的行(称为**非零行**), 从左边起第一个不为0的元素(称为**主元**), 它们的列指标随着行指标的递增而严格增大.

简化阶梯形矩阵的特点:
1. 它是阶梯形矩阵
2. 每个非零行的主元都是1
3. 每个主元所在的列的其余元素都是0

**定理 1** 任意一个矩阵都可以经过一系列初等行变换化成阶梯形矩阵.

**推论 1** 任意一个矩阵都可以经过一系列初等行变换化成简化行阶梯形矩阵.

## 线性方程组的解的情况及其判别准则
**定理 1** 系数为有理数(或实数, 或复数)的 n 元线性方程组的解的情况有三种可能:
* **无解**: 把 n 元线性方程组的增广矩阵经过初等行变换化成阶梯形矩阵, 如果相应的阶梯形方程组出现 $0=d$ (其中 $d$ 是非零数) 这种方程, 那么原方程无解
* **有唯一解**: 如果阶梯形矩阵的非零行数目 r 等于未知量数目 n, 那么原方程组有唯一解
* **有无穷多个解**: 如果 $r \lt n$ 那么原方程组有无穷多个解

如果一个线性方程组有解, 那么称它是**相容**的, 否则,称它是**不相容**的.

常数项全为0的线性方程组称为**齐次线性方程组**. $(0,0,\cdots,0)$ 是齐次线性方程组的一个解, 称为**零解**. 其余的解称为**非零解**. 如果一个齐次线性方程组有非零解, 那么它有无穷多个解. 

**推论 1** n 元齐次线性方程组有非零解的充分必要条件是: 它的系数矩阵经过初等行变换化成的阶梯形矩阵中, 非零行的数目 $r \lt n$.

**推论 2** n 元齐次线性方程组如果方程的数目 s 小于未知量的数目 n, 那么它一定有非零解.

## 数域
**定义 1** 复数集的一个子集 $K$ 如果满足:
1. $0,1 \in K$
2. $a,b \in K \Rightarrow a\pm,ab\in K, \\ a,b \in K, 且 b\neq 0 \Rightarrow \frac{a}{b} \in K$

那么, 称 $K$ 是一个数域.

常见的数域:
* 有理数集: $\mathbb{Q}$
* 实数集: $\mathbb{R}$
* 复数集: $\mathbb{C}$

但整数集 $\mathbb{Z}$ 不是数域, 因为 $\mathbb{Z}$ 对于除法不封闭.

**命题 1** 任意数域都包含有理数域

# 行列式
二阶行列式:
$$
\begin{vmatrix}
    a_{11} && a_{12} \\
    a_{21} && a_{22}
\end{vmatrix}=a_{11}a_{22}-a_{12}a_{21}
$$

**命题 1** 两个方程的二元一次方程组有唯一解的充分必要条件是: 它的系数矩阵 $A$ 的行列式(简称为**系数行列式**) $|\mathbf{A}|\neq 0$, 此时它的唯一解是:
$$
\begin{bmatrix}
    \frac{
        \begin{vmatrix}
            b_1 && a_{12} \\
            b_2 && a_{22}
        \end{vmatrix}
    }{
        \begin{vmatrix}
            a_{11} && a_{12} \\
            a_{21} && a_{22}
        \end{vmatrix}
    }, \frac{
        \begin{vmatrix}
            a_{11} && b_1 \\
            a_{21} && b_2
        \end{vmatrix}
    }{
        \begin{vmatrix}
            a_{11} && a_{12} \\
            a_{21} && a_{22}
        \end{vmatrix}
    }
\end{bmatrix}
$$

## n 元排列
n 个不同的自然数的一个全排列称为一个 **n 元排列**

在 n 元排列 $a_1a_2,\cdots,a_n$ 中, 任取一对数 $a_ia_j$ (其中 $i \lt j$), 如果 $a_i  \lt  a_j$ , 那么称这一对数构成一个**顺序**; 如果 $a_i > a_j$ , 那么称这一对数构成一个**逆序**. 一个 n 元排列中逆序的总数成为**逆序数**, 记作 $\tau(a_1a_2\cdots a_n)$

逆序数为奇数的排列成为**奇排列**, 逆序数为偶数的排列成为**偶排列**.

**定理 1** 对换改变 n 元排列的奇偶性.

**定理 2** 任一 n 元排列与排列 $123\cdots n$ 可以经过一系列对换互变, 并且所对换的次数与这个 n 元排列有相同的奇偶性.

## n 阶行列式的定义
2阶行列式:
$$
\begin{vmatrix}
    a_{11} && a_{12} \\
    a_{21} && a_{22}
\end{vmatrix}=a_{11}a_{22}-a_{12}a_{21}
$$
结合逆序数可写成:
$$
\begin{vmatrix}
    a_{11} && a_{12} \\
    a_{21} && a_{22}
\end{vmatrix}=\sum_{j_1j_2}(-1)^{\tau(j_1j_2)}a_{1j_1}a_{2j_2}
$$

**定义 1** n 阶行列式:
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    a_{21} && a_{22} && \cdots && a_{2n} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=\sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots a_{nj_n}
$$
其中 $j_1j_2\cdots j_n$ 是 n 元排列, $\displaystyle\sum_{j_1j_2\cdots j_n}$ 表示对所有 n 元排列求和. 上式称为 n 阶行列式的**完全展开式**.

令
$$
\mathbf{A}=\begin{bmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    a_{21} && a_{22} && \cdots && a_{2n} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{bmatrix}
$$
则上面的 n 阶行列式也称为 n 级矩阵 $\mathbf{A}$ 的行列式, 简记作 $|\mathbf{A}|$ 或者 $\det \mathbf{A}$

主对角线下方的元素全为0的 n 阶行列式称为**上三角行列式**, 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && a_{13} && \cdots && a_{1,n-2} && a_{1,n-1} && a_{1n} \\
    0 && a_{22} && a_{23} && \cdots && a_{2,n-2} && a_{2,n-1} && a_{2n} \\
    0 && 0 && a_{33} && \cdots && a_{3,n-1} && a_{3,n-1} && a_{3n} \\
    \vdots && \vdots && \vdots && && \vdots && \vdots && \vdots \\
    0 && 0 && 0 && \cdots && 0 && a_{n-1,n-1} && a_{n-1,n} \\
    0 && 0 && 0 && \cdots && 0 && 0 && a_{nn}
\end{vmatrix}
$$
上三角行列式的值为:
$$
(-1)^{\tau(12\cdots n)}a_{11}a_{22}\cdots a_{n-1,n-2}a_{nn}=a_{11}a_{22}\cdots a_{n-1,n-1}a_{nn}
$$

**命题 1** n 阶上三角行列式的值等于它主对角线上 n 个元素的乘积.

## 行列式的性质
**性质 1** 行列互换, 行列式的值不变. 即:
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    a_{21} && a_{22} && \cdots && a_{2n} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=\begin{vmatrix}
    a_{11} && a_{21} && \cdots && a_{n1} \\
    a_{12} && a_{22} && \cdots && a_{n2} \\
    \vdots && \vdots && && \vdots \\
    a_{1n} && a_{2n} && \cdots && a_{nn}
\end{vmatrix}
$$
证明:
$$
右边=\sum_{i_1i_2\cdots i_n}(-1)^{\tau(i_1i_2\cdots i_n)}a_{1i_j}a_{2i_2}\cdots a_{ni_n}
$$
$$
左边=\sum_{i_1i_2\cdots i_n}(-1)^{\tau(i_1i_2\cdots i_n)}a_{1i_j}a_{2i_2}\cdots a_{ni_n}
$$

**性质 2** 行列式一行的公因子可以提出去. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    ka_{i1} && ka_{i2} && \cdots && ka_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=k\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}
$$
证明:
$$
\begin{align*}
左边 &= \sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots(ka_{ij_i})\cdots a_{nj_n} \\
&= k\sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots a_{nj_n} \\
&= 右边
\end{align*}
$$

**性质 3** 行列式中若有某一行是两组数的和, 则此行列式等于两个行列式的和, 这两个行列式的这一行分别是第一组数和第二组数, 而其余各行与原来行列式的各行相同. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    b_1+c_1 && b_2+c_2 && \cdots && b_n+c_n \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=\\\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    b_1 && b_2 && \cdots && b_n \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}+\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    c_1 && c_2 && \cdots && c_n \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}
$$
证明:
$$
\begin{align*}
左边 &= \sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots(b_{j_i}+c_{j_i})\cdots a_{nj_n} \\
&= \sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots b_{j_i}\cdots a_{nj_n} + \sum_{j_1j_2\cdots j_n}(-1)^{\tau(j_1j_2\cdots j_n)}a_{1j_1}a_{2j_2}\cdots c_{j_i}\cdots a_{nj_n}\\
&= 右边
\end{align*}
$$

**性质 4** 两行互换, 行列式反号. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{k1} && a_{k2} && \cdots && a_{kn} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=-\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{k1} && a_{k2} && \cdots && a_{kn} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}
$$

证明:
$$
\begin{align*}
右边 &= -\sum_{j_1\cdots j_i\cdots j_k\cdots j_n}(-1)^{\tau(j_1\cdots j_i\cdots j_k\cdots j_n)}a_{1j_1}\cdots a_{kj_i}\cdots a_{ij_k}\cdots a_{nj_n} \\
&=-\sum_{j_1\cdots j_k\cdots j_i\cdots j_n}(-1)(-1)^{\tau(j_1\cdots j_k\cdots j_i\cdots j_n)}a_{1j_1}\cdots a_{ij_k}\cdots a_{kj_i}\cdots a_{nj_n} \\
&= \sum_{j_1\cdots j_k\cdots j_i\cdots j_n}(-1)^{\tau(j_1\cdots j_k\cdots j_i\cdots j_n)}a_{1j_1}\cdots a_{ij_k}\cdots a_{kj_i}\cdots a_{nj_n} \\
&= 左边
\end{align*}
$$

**性质 5** 两行相同, 行列式的值为0. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=0
$$

**性质 6** 两行成比例, 行列式的值为0. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    la_{i1} && la_{i2} && \cdots && la_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=0
$$

**性质 7** 把一行的倍数加到陵一行上, 行列式的值不变. 即
$$
\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{k1}+la_{i1} && a_{k2}+la_{i2} && \cdots && a_{kn}+la_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}=\begin{vmatrix}
    a_{11} && a_{12} && \cdots && a_{1n} \\
    \vdots && \vdots && && \vdots \\
    a_{i1} && a_{i2} && \cdots && a_{in} \\
    \vdots && \vdots && && \vdots \\
    a_{k1} && a_{k2} && \cdots && a_{kn} \\
    \vdots && \vdots && && \vdots \\
    a_{n1} && a_{n2} && \cdots && a_{nn}
\end{vmatrix}
$$

## 行列式按一行(列)展开
三阶行列式展开为二阶行列式:
$$
\begin{align*}
|\mathbf{A}| &= \begin{vmatrix}
    a_{11} && a_{12} && a_{13} \\
    a_{21} && a_{22} && a_{23} \\
    a_{31} && a_{32} && a_{33}
\end{vmatrix} \\
&= (a_{11}a_{22}a_{33}-a_{11}a_{23}a_{32})+(a_{12}a_{23}a_{33}-a_{12}a_{21}a_{33})+(a_{13}a_{21}a_{32}-a_{13}a_{22}a_{31}) \\
&= a_{11}\begin{vmatrix}
    a_{22} && a_{23} \\
    a_{32} && a_{33}
\end{vmatrix}-a_{12}\begin{vmatrix}
    a_{21} && a_{23} \\
    a_{31} && a_{33}
\end{vmatrix}+a_{13}\begin{vmatrix}
    a_{21} && a_{22} \\
    a_{31} && a_{32}
\end{vmatrix}
\end{align*}
$$

**定义 1** n 阶行列式 $|\mathbf{A}|$ 中, 划去第 i 行和第 j 列, 剩下的元素按照原来的次序组成的行列式成为矩阵 $\mathbf{A}$ 的 $(i,j)$ 元的**余子式**, 记作 $\mathbf{M}_{ij}$. 令
$$
\mathbf{A}_{ij}=(-1)^{i+j}\mathbf{M}_{ij}
$$
则, 三阶行列式的展开可写成:
$$
|\mathbf{A}|=a_{11}\mathbf{A}_{11}+a_{12}\mathbf{A}_{12}+a_{13}\mathbf{A}_{13}
$$

**定理 1** n 阶行列式 $|\mathbf{A}|$ 等于它的第 i 行元素与自己的代数余子式的乘积之和. 即
$$
\begin{align*}
    |\mathbf{A}| &= a_{i1}\mathbf{A}_{i1}+a_{i2}\mathbf{A}_{i2}+\cdots+a_{in}\mathbf{A}_{in} \\
    &= \sum_{j=1}^n a_{ij}\mathbf{A}_{ij}
\end{align*}
$$

**定理 2** n 阶行列式 $|\mathbf{A}|$ 等于它的第 j 列元素与自己的代数余子式的乘积之和. 即
$$
|\mathbf{A}|=|\mathbf{A'}|=a_{1j}\mathbf{A}_{1j}+a_{2j}\mathbf{A}_{2j}+\cdots+a_{nj}\mathbf{A}_{nj}
$$

**定理 3** n 阶行列式 $|\mathbf{A}|$ 第 i 行元素与第 k 行($k\neq i$)相应的元素的代数余子式的乘积之和为0, 即:
$$
a_{i1}\mathbf{A}_{k1}+a_{i2}\mathbf{A}_{k2}+\cdots+a_{in}\mathbf{A}_{kn}\ ,\  当\ k\neq i
$$

**定理 4** n 阶行列式 $|\mathbf{A}|$ 的第 j 列元素与第 l 列($l\neq j$) 的相应元素的代数余子式的乘积之和为0, 即:
$$
a_{1j}\mathbf{A}_{1l}+a_{2j}\mathbf{A}_{2l}+\cdots+a_{nj}\mathbf{A}_{nl}\ ,\  当\ l\neq j
$$

n 阶范德蒙行列式($n>2$)的值为:
$$
\begin{vmatrix}
    1 && 1 && 1 && \cdots && 1 \\
    a_1 && a_2 && a_3 && \cdots && a_n \\
    a_1^2 && a_2^2 && a_3^2 && \cdots && a_n^2 \\
    \vdots && \vdots && \vdots && && \vdots \\
    a_1^{n-2} && a_2^{n-2} && a_3^{n-2} && \cdots && a_n^{n-2} \\
    a_1^{n-1} && a_2^{n-1} && a_3^{n-1} && \cdots && a_n^{n-1}
\end{vmatrix}=\prod_{1\le j \lt \le i\le n}(a_i-a_j)
$$

## 克莱姆(Cramer)法则
对于数域 K 上 n 个方程的 n 元线性方程组, 如何判断有没有解, 有多少解? 方程组:
$$
\left\{\begin{align*}
    a_{11}x_1+a_{12}+\cdots+a_{1n}x_n&=b_1 \\
    a_{21}x_1+a_{22}+\cdots+a_{2n}x_n&=b_2 \\
    \cdots \\
    a_{n1}x_1+a_{n2}+\cdots+a_{nn}x_n&=b_n \\
\end{align*}\right.
$$
令
$$
\mathbf{J}=\begin{bmatrix}
    c_{11} && c_{12} && \cdots && c_{1n} \\
    0 && c_{22} && \cdots && c_{2n} \\
    \vdots && \vdots && && \vdots \\
    0 && 0 && \cdots && c_{nn}
\end{bmatrix}
$$

其中 $c_{11}c_{22},\cdots c_{nn}$ 全不为 0. 从而
$$
|\mathbf{J}|=c_{11}c_{22}\cdots c_{nn}\neq 0
$$
上述表明: 原线性方程组无解或有无穷多个解时, $|\mathbf{J}|=0$, 有唯一解时 $|\mathbf{J}|\neq 0$. 由此得出:
* 原线性方程组有唯一解当且仅当: $|\mathbf{J}|\neq 0$
* $|\mathbf{J}|=l|\mathbf{A}|$  
其中 l 是某个非零数. 因此 $|\mathbf{J}|\neq 0$ 当且仅当 $|\mathbf{A}| \neq 0$. 

**定理 1** 数域 K 上 n 个方程的 n 元线性方程组有唯一解的充分必要条件是它的系数行列式(即系数矩阵 $\mathbf{A}$ 的行列式 $|\mathbf{A}|$) 不等于 0. 如果 $\displaystyle\mathbf{A} \xrightarrow{初等行变换} \mathbf{J}$ 那么 $|\mathbf{J}|=l|\mathbf{A}|$, 其中 l 是某个非零数.

**推论 1** 数域 K 上 n 个方程的 n 元线性方程组只有零解的充分必要条件是它的系数行列式不等于 0. 从而它有非零解的充分必要条件是它的系数行列式等于 0.

两个方程的二元一次方程组有唯一解时, 它的解为: $\displaystyle\left(\frac{|\mathbf{B}_1|}{|\mathbf{A}|}, \frac{|\mathbf{B}_2|}{\mathbf{A}}\right)$, 其中 $B_1,B_2$分别是把系数矩阵 A 的第 1, 2 列换成常数项得到的矩阵. 由此启发: n 个方程的 n 元线性方程组的系数矩阵 A 的第 j 列换成常数项, 得到的矩阵记作 $\mathbf{B}_j, j=1,2,\cdots,n$, 即
$$
\mathbf{B}_j=\begin{bmatrix}
    a_{11} && \cdots && a_{1,j-1} && b_1 && a_{1,j+1} && \cdots && a_{1n} \\
    a_{21} && \cdots && a_{2,j-1} && b_1 && a_{2,j+1} && \cdots && a_{2n} \\
    \vdots && && \vdots && \vdots && \vdots && && \vdots \\
    a_{n1} && \cdots && a_{n,j-1} && b_n && a_{n,j+1} && \cdots && a_{nn} \\
\end{bmatrix}
$$

**定理 2** n 个方程的 n 元线性方程组的系数行列式 $|\mathbf{A}|\neq 0$ 时, 它的唯一解是:
$$
\left(\frac{|\mathbf{B}_1|}{|\mathbf{A}|}, \frac{|\mathbf{B}_2|}{\mathbf{A}},\cdots,\frac{|\mathbf{B}_n|}{\mathbf{A}}\right)
$$

**定理 1** 和 **定理 2** 合起来称为**克莱姆(Cramer)法则**

## 行列式按 k 行(列) 展开
**定义 1** n 阶行列式 $|\mathbf{A}|$ 中任意取定 k 行, k 列 ( $1 \le k \lt n$ ), 位于这些行列的交叉处的 $k^2$ 个元素按照原来的排法组成的 k 阶行列式, 称 $|\mathbf{A}|$ 的一个 **k 阶子式**. 取定 $|\mathbf{A}|$ 的第 $i_1,i_2,\cdots,i_k$ 行 ($i_1 \lt i_2 \lt \cdots \lt i_k$), 第 $j_1,j_2,\cdots,j_k$ 列 ($j_1 \lt j_2 \lt \cdots \lt j_k$), 所得到的 k 阶子式记作:
$$
\mathbf{A}\begin{pmatrix}
    i_1,i_2,\cdots,i_k \\
    j_1,j_2,\cdots,j_k
\end{pmatrix}
$$
划去这个 k 阶子式所在的行和列, 剩下的元素按照原来的排法组成的 $(n-k)$ 阶行列式称为上述子式的余子式, 它前面乘以
$$
(-1)^{(i_1+i_2+\cdots+i_k)+(j_1+j_2+\cdots+j_k)}
$$
则称为上述子式的代数余子式. 令
$$
\begin{align*}
    \{i_1',i_2',\cdots,i_{n-k}'\} &= \{1,2,\cdots,n\}\backslash\{i_1,i_2,\cdots,i_k\} \\
    \{j_1',i_2',\cdots,j_{n-k}'\} &= \{1,2,\cdots,n\}\backslash\{j_1,j_2,\cdots,j_k\}
\end{align*}
$$
并且 $i_1'\lt i_2' \lt\cdots\lt i_{n-k}', j'\lt j_2'\lt\cdots\lt j_{n-k}'$, 则余子式为:
$$
\mathbf{A}\begin{pmatrix}
    i_1',i_2',\cdots,i_{n-k}' \\
    j_1',j_2',\cdots,j_{n-k}'
\end{pmatrix}
$$

**定理 1(Laplace定理)** 在 n 阶行列式 $|\mathbf{A}|$ 中, 取定第 $i_1,i_2,\cdots,i_k$ 行 ($i_1 \lt i_2 \lt \cdots \lt i_k$), 则这 k 行元素所形成的所有 k 阶子式与他们自己的代数余子式的乘积之和等于 $|\mathbf{A}|$, 即:
$$
|\mathbf{A}|=\sum_{1\le j_1 \lt j_2 \lt \cdots \lt j_k\le n}\mathbf{A}\begin{pmatrix}
    i_1,i_2,\cdots,i_k \\
    j_1,j_2,\cdots,j_k
\end{pmatrix}(-1)^{(i_1+\cdots+i_k)+(j_1+\cdots+j_k)}\begin{pmatrix}
    i_1',i_2',\cdots,i_k' \\
    j_1',j_2',\cdots,j_k'
\end{pmatrix}
$$

# 线性方程组的解集的结构
## n 维向量空间 $\mathbb{K}^n$
取定一个数域 $\mathbb{K}$, 设 n 是任意给定的一个正整数. 令
$$
\mathbb{K}^n=\{(a_1,a_2,\cdots,a_n)\mid a_i \in \mathbb{K},i=1,2,\cdots,n\}
$$
如果 $a_1=b_1,a_2=b_2,\cdots,a_n=b_n$, 则称 $\mathbb{K}^n$ 中两个元素 $(a_1,a_2,\cdots,a_n)$ 与 $(b_1,b_2,\cdots,b_n)$ 相等. 

在 $\mathbb{K}^n$ 中规定加法运算如下:
$$
(a_1,a_2,\cdots,a_n) + (b_1,b_2,\cdots,b_n) \\
\xlongequal{\mathrm{def}}(a_1+b_1,a_2+b_2,\cdots,a_n+b_n)
$$
在 $\mathbb{K}$ 的元素与 $\mathbb{K}^n$ 的元素之间规定的数量乘法运算如下:
$$
k(a_1,a_2,\cdots,a_n) \xlongequal{\mathrm{def}}(ka_1,ka_2,\cdots,ka_n)
$$

容易直接验证加法和数量乘法满足如下8条运算法则: 对于 $\vec{\alpha}, \vec{\beta}, \vec{\gamma} \in \mathbb{K}$, 有:
1. $\vec{\alpha} + \vec{\beta} = \vec{\beta} + \vec{\alpha}$
2. $(\vec{\alpha} + \vec{\beta}) + \vec{\gamma} = \vec{\alpha} + (\vec{\beta} + vec{\gamma})$
3. 把元素 $(0,0,\cdots,0)$ 记作 $\vec{0}$, 它使得:
$$
\vec{0} + \vec{a} = \vec{a} + \vec{0} = \vec{a}
$$
称 $\vec{0}$ 是 $\mathbb{K}$ 的零元素.

4. 对于 $\vec{a}=(a_1,a_2,\cdots,a_n) \in \mathbb{K}^n$, 令
$$
-\vec{a}\xlongequal{\mathrm{def}}(-a_1,-a_2,\cdots,-a_n) \in \mathbb{K}^n
$$
有
$$
\vec{\alpha} + (-\vec{\alpha}) = (-\vec{\alpha})+\vec{\alpha}=\vec{0}
$$
5. $1\vec{\alpha}=\vec{\alpha}$
6. $(kl)\vec{\alpha}=k(l\vec{\alpha})$
7. $(k+l)\vec{\alpha}=k\vec{\alpha}+l\vec{\alpha}$
8. $k(\vec{\alpha} + \vec{\beta}) = k\vec{\alpha}+k\vec{\beta}$

**定义 1** 数域 $\mathbb{K}$ 上所有 n 元有序数组组成的集合 $\mathbb{K}^n$, 连同定义在它上面的加法运算和数量乘法运算, 及其满足的 8 条运算法则一起, 称为数域 $\mathbb{K}$ 上的一个 **n 维向量空间**. $\mathbb{K}^n$ 的元素称为 **n维向量**. 设向量 $\vec{a}=(a_1,a_2,\cdots,a_n)$ , 称 $a_i$ 是 $\vec{a}$ 的第 $i$ 个**分量**.

通常用小写希腊字母 $\vec{\alpha}, \vec{\beta}, \alpha{\beta} \cdots$ 表示向量.

在 n 维向量空间 $\mathbb{K}^n$ 中, 可以定义减法运算如下:
$$
\vec{\alpha}-\vec{\beta}\xlongequal{\mathrm{def}}\vec{\alpha} + (-\vec{\beta})
$$

在 n 维向量空间 $\mathbb{K}^n$ 中, 容易直接验证下述 4 条性质:
1. $0\vec{\alpha}=\vec{0}, \forall \vec{\alpha} \in \mathbb{K}^n$
2. $(-1)\vec{\alpha}=-\vec{\alpha}, \forall \vec{\alpha} \in \mathbb{K}^n$
3. $k\vec{0}=\vec{0}, \forall k \in \mathbb{K}$
4. $k\vec{\alpha} \Rightarrow k=0 或 \vec{\alpha}=\vec{0}$

n 元有序数组写成一行 $(a_1,a_2,\cdots,a_n)$, 称为**行向量**. 写成一列:
$$
\begin{bmatrix}
    a1 \\ a2 \\ \vdots \\ a_n
\end{bmatrix}
$$
称为**列向量**. 列向量可以看成是相应的行向量的转置. 列向量可写成 $(a_1,a_2,\cdots,a_n)'$

$\mathbb{K}^n$ 可以看成是 n 维行向量组成的向量空间, 也可以看成是 n 维列向量组成的向量空间.

在 $\mathbb{K}^n$ 中, 由于加法和数量乘法两种运算, 给定向量组: $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$, 任给 $\mathbb{K}$ 中一组数 $k_1,k_2,\cdots,k_s$, 就可以得到一个向量 $k_1\vec{\alpha}_1,k_2\vec{\alpha}_2,\cdots,k_s\vec{\alpha}_s$, 称这个向量是向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_n$ 的一个线性组合, 其中 $k_1,k_2,\cdots,k_s$ 称为 **系数**.

在 $\mathbb{K}$ 中, 给定向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$, 对于 $\vec{\beta}\in \mathbb{K}^n$ 如果存在 $\mathbb{K}$ 中一组数 $c_1, c_2, \cdots, c_s$ 使得:
$$
\vec{\beta}=c_1\vec{\alpha}_1+c_2\vec{\alpha}_2+\cdots+c_s\vec{\alpha}_s
$$
那么称 $\vec{\beta}$ 可以由 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ **线性表出**
利用向量的加法运算和乘法元算, 可以把数域 $\mathbb{K}$ 上 n 元线性方程组
$$
\left\{\begin{align*}
    a_{11}x_1+a_{12}+\cdots+a_{1n}x_n&=b_1 \\
    a_{21}x_1+a_{22}+\cdots+a_{2n}x_n&=b_2 \\
    \cdots \\
    a_{s1}x_1+a_{s2}+\cdots+a_{sn}x_n&=b_s \\
\end{align*}\right.
$$
写成:
$$
x_1\begin{bmatrix}
    a_{11} \\ a_{21} \\ \vdots \\ a_{s1}
\end{bmatrix}+x_2\begin{bmatrix}
    a_{12} \\ a_{22} \\ \vdots \\ a_{s2}
\end{bmatrix}+\cdots+x_n\begin{bmatrix}
    a_{1n} \\ a_{2n} \\ \vdots \\ a_{sn}
\end{bmatrix}=\begin{bmatrix}
    b_1 \\ b_2 \\ \vdots \\ b_s
\end{bmatrix}
$$
即: $x_1\vec{\alpha}_1+x_2\vec{\alpha}_2+\cdots x_n\vec{\alpha}_n=\vec{\beta}$

其中 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_n$ 是线性方程组的系数矩阵的列向量组. $\vec{\beta}$ 是由常数项组成的列向量. 于是

数域 $\mathbb{K}$ 上线性方程组 $x_1\vec{\alpha}_1+x_2\vec{\alpha}_2+\cdots x_n\vec{\alpha}_n=\vec{\beta}$ 有解 $\xLeftrightarrow{}$ $\mathbb{K}$ 中存在一组书 $c_1,c_2,\cdots,c_n$ 使得下式成立:
$$
c_1\vec{\alpha}_1+c_2\vec{\alpha}_2+\cdots+c_s\vec{\alpha}_s=\vec{\beta}
$$
$\xLeftrightarrow{}$ $\vec{\beta}$可以由 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_n$ 线性表出.

把向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ 的所有线性组合组成一个组合 $\mathbf{W}$ 即
$$
\mathbf{W}\xlongequal{\mathrm{def}}=\{k_1\vec{\alpha}_1+k_2\vec{\alpha}_2+\cdots+k_s\vec{\alpha}_s \mid k_i \in \mathbb{K}, i=1,2,\cdots,s\}
$$

研究 $\mathbf{W}$ 的结构, 任取 $\vec{\alpha},\vec{\gamma} \in \mathbf{W}$ 设
$$
\vec{\alpha}=a_1\vec{\alpha}_1+a_2\vec{\alpha}_2+\cdots+a_s\vec{\alpha}_s=b_1\vec{\alpha}_1+b_2\vec{\alpha}_2+\cdots+b_s\vec{\alpha}_s
$$
则:
$$
\vec{\alpha}+\vec{\gamma}+(a_1+b_1)\vec{\alpha}_1+(a_2+b_2)\vec{\alpha}_2+\cdots+(a_s+b_s)\vec{\alpha}_s \in \mathbf{W} \\
k\vec{\alpha}=(ka_1)\vec{\alpha}_1+(ka_2)\vec{\alpha}_2+\cdots+(ka_s)\vec{\alpha}_s \in \mathbf{W}
$$

其中 $k$ 是 $\mathbb{K}$ 中的任意数. 

**定义 2** $\mathbb{K}^n$ 的一个非空子集 $\mathbf{U}$ 如果满足:
* $\vec{\alpha}, \vec{\gamma} \in \mathbf{U} \Rightarrow \vec{\alpha}+\vec{\gamma} \in \mathbf{U}$
* $\vec{\alpha} \in \mathbf{U}, k \in \mathbb{K} \Rightarrow k\vec{\alpha} \in \mathbf{U}$

那么称 $\mathbf{U}$ 是 $\mathbb{K}^n$ 的一个**线性子空间**.

$\{\vec{0}\}$ 是 $\mathbb{K}^n$ 的一个线性子空间, $\mathbb{K}^n$ 本身也是 $\mathbb{K}^n$ 的一个线性子空间. $\mathbb{K}^n$ 中 向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ 的所有线性组合组成的集合 $\mathbf{W}$ 是 $\mathbb{K}^n$ 的一个子空间, 称他为 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$, **生成(或张成)的子空间** 记作
$$
\langle\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s\rangle
$$

**命题 1** 数域 $\mathbb{K}$ 上 n 元线性方程组 $x_1\vec{\alpha}_1+x_2\vec{\alpha}_2+\cdots+x_n\vec{\alpha}_n=\vec{\beta}$ 有解  
$\Rightarrow$ $\vec{\beta}$ 可以由 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_n$ 线性标出  
$\Rightarrow$ $\vec{\beta} \in \langle\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s\rangle$

## 线性相关与线性无关向量组
结合空间 $\mathbf{V}$ (由所有以原点为起点的向量组成) 中, 取定三个不共面的向量 $\vec{e}_1,\vec{e}_2,\vec{e}_3$, 则 $\mathbf{V}$ 中每一个向量 $\vec{a}$ 都可以由 $\vec{e}_1,\vec{e}_2,\vec{e}_3$ 唯一的线性表出:
$$
\vec{a}=a_1\vec{e}_1+a_2\vec{e}_2+a_3\vec{e}_3
$$

从解析几何中, 我们知道:
* $\vec{e}_1,\vec{e}_2,\vec{e}_3$ 共面的充分必要条件是有不全为0的实数 $k_1,k_2,k_3$ 使得
$$
k_1\vec{a}_1+k_2\vec{a}_2+k_3\vec{a}_3=\vec{0}
$$
* $\vec{e}_1,\vec{e}_2,\vec{e}_3$ 不共面的充分必要条件是: 从
$$
k_1\vec{a}_1+k_2\vec{a}_2+k_3\vec{a}_3=\vec{0}
$$
  可以推出 $k_1=0,k_2=0,k_3=0$

**定义 1** $\mathbb{K}^n$ 中向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s (s\ge 1)$ 成为是线性相关的, 如果 $\mathbb{K}$ 中有不全为0的数 $k_1,\cdots,k_s$ 使得
$$
k_1\vec{\alpha}_1+\cdots+k_s\vec{\alpha}_s=\vec{0}
$$

**定义 2** $\mathbb{K}^n$ 中向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s (s\ge 1)$ 如果不是线性相关的, 那么称为**线性无关**的. 即如果从
$$
k_1\vec{\alpha}_1+\cdots+k_s\vec{\alpha}_s=\vec{0}
$$
可以推断出所有系数 $k_1,\cdots,k_s$ 全为 0, 那么称向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s$ 是线性无关的.

根据定义 1/2 可以立刻得到:
* 包含零向量的向量组一定线性相关(因为 $1\vec{0}+0\vec{\alpha}_2+\cdots+0\vec{\alpha}_s=0$)
* 单个向量 $\vec{\alpha}$ 线性相关当且仅当 $\vec{\alpha}=\vec{0},k\neq0 \Leftrightarrow \vec{\alpha}=\vec{0}$; 从而单个向量 $\vec{\alpha}$ 线性无关当且仅当 $\vec{\alpha}\neq\vec{0}$
* $\mathbb{K}^n$ 中, 向量组
$$
\vec{\epsilon}_1=\begin{bmatrix}
    1 \\ 0 \\ 0 \\ \vdots \\ 0 \\ 0
\end{bmatrix},\vec{\epsilon}_2=\begin{bmatrix}
    0 \\ 1 \\ 0 \\ \vdots \\ 0 \\ 0
\end{bmatrix},\cdots,\vec{\epsilon}_n=\begin{bmatrix}
    0 \\ 0 \\ 0 \\ \vdots \\ 0 \\ 1
\end{bmatrix}
$$
是线性无关的(因为从 $k_1\vec{\epsilon}_1+k_2\vec{\epsilon}_2+\cdots+k_n\vec{\epsilon}_n=\vec{0}$ 可得出 $k_1=k_2=\cdots=k_n=0$)

<!-- 几个角度来考察线性相关的向量组与线性无关的向量组的本质区别:
* 从线性组合角度看:
  向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s(s\ge 1)$ 线性相关  
  $\Leftrightarrow$ 它们有系数不全为0的线性组合等于零向量;

  向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s(s\ge 1)$ 线性无关  
  $\Leftrightarrow$ 他们只有系数全为0的线性组合才会等于零向量.
  
* 从线性表出看:
  向量组 $\vec{\alpha}_1, \vec{\alpha}_2,\cdots,\vec{\alpha}_s(s\ge 2)$ 线性相关  
  $\Leftrightarrow$ 其中至少有一个向量可以有其余向量线性表出
 -->

**命题 1** 设向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s$ 线性无关, 则向量 $\vec{\beta}$ 可以由 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s$ 线性表出的充分必要条件是: $\vec{\alpha}_1,\cdots,\vec{\alpha}_s,\vec{\beta}$ 线性相关.

**推论 1** 设向量组 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s$ 线性无关, 则向量 $\vec{\beta}$ 不能由 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s$ 线性表出的充分必要条件是 $\vec{\alpha}_1,\cdots,\vec{\alpha}_s,\vec{\beta}$ 线性无关.

## 向量的秩
**定义 1** 向量组的一个部分组成为一个**极大线性无关组**, 如果这个部分本身是线性无关的, 但是从这个向量组的其余向量(如果还有的话)中任取一个添进去, 得到的新的部分组都线性相关.

**定义 2** 如果向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 的每一个向量都可以由向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 线性表出, 那么称向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 可以由向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 线性表出.如果向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 与向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 可以互相线性表出, 那么称向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 与向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 等价, 记作:
$$
\{\vec{\alpha},\cdots,\vec{\alpha}_s\} \cong \{\vec{\beta},\cdots,\vec{\beta}_r\}
$$
向量组的等价是向量组之间的一种关系. 可以证明, 这种关系具有下述三种性质:
* 反身性. 即任何一个向量组都与自身等价
* 对称性. 即如果 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 与 $\vec{\beta},\cdots,\vec{\beta}_r$ 等价, 那么 $\vec{\beta},\cdots,\vec{\beta}_r$ 与 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 等价
* 传递性. 即如果
$$
\{\vec{\alpha},\cdots,\vec{\alpha}_s\} \cong \{\vec{\beta},\cdots,\vec{\beta}_r\},\{\vec{\beta},\cdots,\vec{\beta}_r\} \cong \{\vec{\gamma},\cdots,\vec{\gamma}_t\}
$$
那么
$$
\{\vec{\alpha},\cdots,\vec{\alpha}_s\} \cong \{\vec{\gamma},\cdots,\vec{\gamma}_t\}
$$

关于传递性, 只需证明线性表出有传递性: 设 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 可以由 $\vec{\beta},\cdots,\vec{\beta}_r$ 线性表出:
$$
\vec{\alpha}_i=\sum_{j=1}^r b_{ij}\vec{\beta}_j, j=1,\cdots,s
$$
且 $\vec{\beta},\cdots,\vec{\beta}_r$ 可以由 $\vec{\gamma},\cdots,\vec{\gamma}_t$ 线性表出:
$$
\vec{\beta}_j=\sum_{l=1}^t c_{jl}\vec{\gamma}_l, j=1,\cdots,s
$$
则:
$$
\vec{\alpha}_i=\sum_{j=1}^r b_{ij}(\sum_{l=1}^t c_{jl}\vec{\gamma}_l)=\sum_{j=1}^r (\sum_{l=1}^t b_{ij}c_{jl})\vec{\gamma}_l, i=1,\cdots,s
$$
即 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 可以由 $\vec{\gamma},\cdots,\vec{\gamma}_t$ 线性表出

**推论 1** 向量组的任意两个极大线性无关组等价

**推论 2** $\vec{\beta}$ 可以由向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 线性表出当且仅当 $\vec{\beta}$ 可以由 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 的一个极大线性无关组线性表出.

**引理 1** 设向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 可以由向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 线性表出, 如果 $r\gt s$, 那么 $\vec{\beta},\cdots,\vec{\beta}_r$ 线性相关.

**推论 3** 设向量组 $\vec{\beta},\cdots,\vec{\beta}_r$ 可以由向量组 $\vec{\alpha},\cdots,\vec{\alpha}_s$ 线性表出, 如果 $\vec{\beta},\cdots,\vec{\beta}_r$ 线性无关, 那么 $r \le s$

**推论 4** 等价的线性无关向量组所含向量的个数相等.

**推论 5** 向量组的任意两个极大线性无关组所含向量的个数相等.

**定义 3** 向量组的极大线性无关组所含向量的个数称为这个**向量组的秩**. 

全由零向量组成的向量组的秩规定为 0

向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ 的秩记作 $\mathrm{rank}\{\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s\}$

**命题 2** 向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ 线性无关的充分必要条件是它的秩等于它所含向量的个数.

**命题 3** 如果向量组(I)可以由向量组(II)线性表出, 那么:
$$
(I) 的秩 \le (II) 的秩
$$

**命题 4** 等价的向量组有相等的秩

## 子空间的基与维数
**定义 1** 设 $\mathbf{U}$ 是 $\mathbb{K}^n$ 的一个子空间, 如果 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r \in \mathbf{U}$, 并且满足下述两个条件:
* $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r$ 线性无关
* $\mathbf{U}$ 中每一个向量都可以由 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r$ 线性表出

那么称 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r$ 是 $\mathbf{U}$ 的一个基.

** 定理 1** $\mathbb{K}^n$ 的任一非零子空间 $\mathbf{U}$ 都有一个基.

**定理 2** $\mathbb{K}^n$ 的非零子空间 $\mathbf{U}$ 的任意两个基所含向量的个数相等.

**定义 2** $\mathbb{K}^n$ 的非零子空间 $\mathbf{U}$ 的一个基所含向量的个数称为 $\mathbf{U}$ 的维数, 记作 $\dim_K \mathbf{U}$ 或 $\dim \mathbf{U}$

**命题 1** 设 $\dim \mathbf{U}=r$, 则 $\mathbf{U}$ 中任意 $r+1$ 个向量都线性相关.

**命题 2** 设 $\dim \mathbf{U}=r$, 则 $\mathbf{U}$ 中任意 $r$ 个线性无关的向量都是 $\dim \mathbf{U}=r$ 的一个基.

**命题 3** 设 $\dim \mathbf{U}=r$, 设 $\vec{\alpha},\cdots,\vec{\alpha}_r \in \mathbf{U}$. 如果 $\mathbf{U}$ 中每一个向量都可以由 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r$ 线性表出, 那么 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_r$ 是 $\mathbf{U}$ 的一个基.

**命题 4 设 $\dim \mathbf{U}$ 和 $\dim \mathbf{W}$ 都是 $\mathbb{K}^n$ 的非零子空间, 如果 $\mathbf{U} \subseteq \mathbf{W}$ 那么
$$
\dim \mathbf{U} \le \dim \mathbf{W}
$$

**命题 5** 设 $\dim \mathbf{U}$ 和 $\dim \mathbf{W}$ 都是 $\mathbb{K}^n$ 的非零子空间, 且 $\mathbf{U} \subseteq \mathbf{W}$ 如果 $\dim \mathbf{U} = \dim \mathbf{W}$ 那么 $\mathbf{U}=\mathbf{W}$

**定理 3** 向量组 $\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s$ 的一个极大线性无关组是这个向量组生成的子空间 $\langle \vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s\rangle$ 的一个基, 从而
$$
\dim \vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s = \mathrm{rank} \{\vec{\alpha}_1,\vec{\alpha}_2,\cdots,\vec{\alpha}_s\} 
$$

