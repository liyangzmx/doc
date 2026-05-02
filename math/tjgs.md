# 高等数学（同济版）

## 第一章 · 函数与极限

## 映射与函数
### 映射
#### 映射的概念
**定义** 设 $X,Y$ 是两给非空集合, 如果存在一个法则 $\displaystyle f$ 使得 $X$ 中每个元素 $x$ ,按法则 $f$, 在 Y 中有唯一确定的元素 $y$ 与之对应, 那么称 $f$ 为从 X 到 Y 的**映射**. 记作
```math
f:X\to Y
```
其中 $y$ 称为元素 $x$ (在映射 $f$ 下)的像, 并记作 $f(x)$, 即:
```math
y=f(x)
```

而元素 $x$ 称为元素 $y$ (在映射 f) 下的一个**原像**, 集合 X 称为映射 f 的定义域, 记作 $D_f$, 即 $D_f=X$; X 中所有元素的像所组成的集合称为映射 f 的值域, 记作 $R_f$ 或 $f(X)$, 即:
```math
R_f=f(X)=|f(x)|mid x\in X|
```

逆映射与复合映射
设 f 是 X 到 Y 的映射, 则由定义, 对于每个 $y\in R_f$, 有唯一的 $x\in X$, 适合 $f(x)=y$, 于是, 我们可以定义一个从 $R_f$ 到 X 的新映射 g 即:
```math
g:R_f \to X
```
对于每个 $y\in R_f$, 规定 $g(y)=x$, 这 x 满足 $f(x)=y$. 这个映射 g 称为 f 的**逆映射**, 记作 $f^{-1}$, 其定义域 $D_{f^{-1}}=R_f$, 值域 $R_{f^{-1}}=X$.

### 函数
#### 函数的概念
**定义** 设数集 $\mathbf{D}\subset \mathbb{R}$, 则称映射 $f:\mathbf{D}\to\mathbb{R}$ 为定义在 $\mathbf{D}$ 上的**函数**, 通常简记为:
```math
y=f(x), x\in \mathbf{D}
```
其中 x 称为**自变量**, y 称为**因变量**, D 称为**定义域**, 记作 $D_f$, 即 $D_f=D$.

#### 函数的几种特性
1) **函数的有界性** 设函数 $f(x)$ 的定义域为 D, 数集 $X\in\mathbf{D}$ 如果存在数 $K_1$ 使得
```math
f(x) \le K_1
```
对于任意 $x\in X$ 都成立, 那么函数 $f(x)$ 在 X 上有**上界**, 而 $K_1$ 称为函数的一个上界. 如果存在数 $K_2$ 使得:
```math
f(x)\ge K_2
```
对于任意 $x\in X$ 都成立, 那么函数 $f(x)$ 在 X 上有**下界**, 而 $K_2$ 称为函数的一个下界.

2) **函数的单调性** 设函数 $f(x)$ 的定义域为 $D$, 区间 $I\subset D$. 如果对于区间 $I$ 上任意两点 $x_1$ 及 $x_2$ 当 $x_1 \lt x_2$ 是恒有:
```math
f(x_1) \lt f(x_2)
```
那么称函数 f(x) 在区间 I 上是**单调增加**的. 如果对于区间 $I$ 上任意两点 $x_1$ 及 $x_2$ 当 $x_1 \lt x_2$ 是恒有:
```math
f(x_1) \gt f(x_2)
```
那么称函数 f(x) 在区间 I 上是**单调减少**的. 单调增加和单调减少函数统称为单调函数.

3) **函数的奇偶性** 设函数 f(x) 的定义域 D 关于原点对称. 如果对于任一 $x\in D$:
```math
f(-x)=f(x)
```
恒成立, 那么称 f(x) 为偶函数. 如果对于任一 $x\in D$:
```math
f(-x)=-f(x)
```
恒成立, 那么称 f(x) 为奇函数. 

4) **函数的周期性** 设函数 f(x) 的定义域为 D. 如果存在一个正数 l , 使得对于任意 $x\in D$ 有 $(x\pm)\in D$ 且
```math
f(x+l)=f(x)
```
恒成立, 那么称 f(x) 为周期函数, l 称为 f(x) 的周期, 通常我们说说周期函数的周期是最小正周期.

#### 反函数与复合函数
设函数 $f:D\to f(D)$ 是单射, 则它存在逆映射 $f^{-1}:f(D) \to D$, 称映射 $f^{-1}$ 为函数 $f$ 的反函数. 对于每个 $y \in f(D)$ 有唯一的 $x\in D$ 使得 $f(x)=y$, 于是有:
```math
f^{-1}(y)=x
```

#### 函数的运算
设函数 $f(x),g(x)$ 的定义域以此为 $D_f,D_g,D=D_f\cap\neq\emptyset$, 则我们可以定义这两个函数的下列运算:
* 和(差) $f\pm g:\ \ \ \ \ \ (f\pm g)(x)=f(x)\pm g(x),x \in D$
* 积 $f\cdot g:\ \ \ \ \ \ (f\cdot g)(x)=f(x)\cdot g(x), x\in D$
* 商 $\displaystyle\frac{f}{g}:\ \ \ \ \ \ \displaystyle\left(\frac{f}{g}\right)(x)=\frac{f(x)}{g(x)}, x\in D \backslash \{x\mid g(x)=0,x\in D\}$

#### 初等函数
幂函数: $y=x^\mu (\mu \in \mathbb{R} 是常数)$  
指数函数: $y=a^x (a \gt 0 且 a \neq 1)$  
对数函数: $y=\log_{a}x(a\gt 0 且 a\neq 1, 特别当 a=\mathrm{e} 时, 记为 y=\ln x)$  
三角函数: 如 $y=\sin x,y=\cos x,y=\tan x$ 等  
反三角函数: 如 $y=\arcsin x, y=\arccos x,y=\arctan x$ 等

以上这五类函数统称为基本初等函数.

由常数和基本初等函数经过有限次的四则元算和有限次的函数复合步骤所构成并可用一个式子表示的函数称为**初等函数**. 例如:
```math
y=\sqrt{1-x^2}, y=\sin^2x,y=\sqrt{\cot \frac{x}{2}}
```
等都是初等函数.

应用上常遇到以 $\mathrm{e}$ 为底的指数函数 $y=\mathrm{e}^x$ 和 $y=\mathrm{e}^{-x}$ 所产生的双曲函数以及它们的反函数:反双曲函数, 它们的定义如下:
* 双曲正弦: $\displaystyle\mathrm{sh} x = \frac{e^x-e^{-x}}{2}$
* 双曲余弦: $\displaystyle\mathrm{ch} x = \frac{e^x+e^{-x}}{2}$
* 双曲正切: $\displaystyle\mathrm{th} x = \frac{\mathrm{sh} x}{\mathrm{ch} x} = \frac{e^x-e^{-x}}{e^x+e^{-x}}$

根据双曲函数的定义, 可证如下四个公式:
* $\mathrm{sh} (x + y) = \mathrm{sh} x \mathrm{ch} y + \mathrm{ch} x \mathrm{sh} y$
* $\mathrm{sh} (x - y) = \mathrm{sh} x \mathrm{ch} y - \mathrm{ch} x \mathrm{sh} y$
* $\mathrm{ch} (x + y) = \mathrm{ch} x \mathrm{ch} y + \mathrm{sh} x \mathrm{sh} y$
* $\mathrm{ch} (x - y) = \mathrm{ch} x \mathrm{ch} y - \mathrm{sh} x \mathrm{sh} y$

双曲函数 $y=\mathrm{sh} x, y=\mathrm{ch} x(x\ge0),y=\mathrm{th} x$ 的反函数依次记为:
* 反双曲正弦: $y=\mathrm{arsh} x$
* 反双曲余弦: $y=\mathrm{arch} x$
* 反双曲正切: $y=\mathrm{arth} x$

先讨论双曲正弦 $y=\mathrm{sh} x$ 的反函数. 由 $x=\mathrm{sh} y$ 有
```math
x=\frac{e^y-e^{-y}}{2}
```

令 $u=e^y$, 则由上式有
```math
u^2-2xu-1=0
```
这是关于 u 的一个二次方程, 它的根为:
```math
u=x\pm\sqrt{x^2+1}
```
因 $u=e^y \gt 0$, 故上式根号前应取正号, 于是:
```math
u=x+\sqrt{x^2+1}
```
由于 $y=\ln u$, 故得反双曲正弦:
```math
y=\mathrm{arsh}x=\ln(x+\sqrt{x^2+1})
```
函数 $y=\mathrm{arsh}x$ 的定义域为: $(-\infty, \infty)$ , 它是奇函数, 在区间 $(-\infty, \infty)$ 内为单调增加.

类似的, 反双曲余弦函数:
```math
y=\mathrm{arch}x=\ln(x+\sqrt{x^2+1})
```

反双曲正切:
```math
y=\mathrm{arth}x=\frac{1}{2}\ln \frac{1+x}{1-x}
```

## 数列的极限
### 数列极限的定义
如果按照某一法则, 对于每个 $n\in \mathbb{N}_+$, 对应着一个确定的实数 $x_n$, 这些实数 $x_n$ 按照下标从小到大排列得到的一个序列
```math
x_1,x_2,x_3,\cdots,x_n,\cdots
```
就叫做数列, 简记为数列 $|x_n|$

数列中的每一个数叫做列的项, 第 n 项 $x_n$ 叫做数列的**一般项**(或**通项**).

数列 $\{x_n\}$ 恶可以看作自变量为正整数 n 的函数:
```math
x_n=f(n),n\in \mathbb{N}_+
```
当自变量 n 依次取 $1,2,3,\cdots$ 一切正整数时, 对应的函数值就排列成数列 $\{x_n\}$

**定义** 设 $\{x_n\}$ 为一数列, 如果存在常数 $a$, 对于任意给定的正数 $\epsilon$ (无论多么小), 总存在正整数 $N$ 使得当 $n\gt N$ 时, 不等式
```math
|x_n-a|\le \epsilon
```
都成立, 那么就称常数 $a$ 是数列 $\{x_n\}$ 的**极限**, 或者称数列 $\{x_n\}$ 收敛于 $a$, 记为
```math
\lim_{n\to \infty}x_n=a
```
或
```math
x_n\to a(n \to \infty)
```

为了表达方便, 引入记号 " $\forall$ " 表示 "对于任意给定的" 或 "对于每一个", 记号 " $\exists$ " 表示 "存在". 于是, "对于任意给定的 $\epsilon \gt 0$"写成: " $\forall\epsilon\gt 0$ ", " 存在正整数 $N$ " 写成 " $\exists正整数N$ ", 数列极限 $\displaystyle\lim_{n\to\infty}x_n=a$ 的定义可表达为:
```math
\lim_{n\to\infty}x_n=a \Leftrightarrow \forall\epsilon\gt 0, \exists 正整数 N, 当 n \gt N 时, 有 |x_n-a|\le\epsilon
```

### 收敛数列的性质
**定理 1(极限的唯一性)** 如果数列 $\{x_n}$ 收敛, 那么它的极限唯一.

**定理 2(收敛数列的有界性)** 如果数列 $\{x_n\}$ 收敛, 那么数列 $\{x_n\}$ 一定有界. 

**定理 3(收敛数列的保号性)** 如果 $\displaystyle\lim_{n\to\infty}=a, 且 a \gt 0(或 a \lt 0)$, 那么存在正整数 $N$, 当 $n \gt N$ 时, 都有 $x_n\gt 0 (或 x_n \lt 0)$

**推论** 如果数列 $\{x_n\}$ 从某项起有 $x_n \ge 0$(或 $x_n \le 0$), 且 $\displaystyle\lim_{x\to\infty}x_n=a$, 那么 $a\gt 0$(或 $a\le 0$)

**定理 4(收敛数列与其子数列间的关系)** 如果数列 $\{x_n\}$ 收敛于 $a$, 那么它的任一子序列也收敛, 且极限也是 $a$

## 函数的极限
### 函数极限的定义
#### 自变量趋于有限值时函数的极限
**定义 1** 设函数 $f(x)$ 在点 $x_0$ 的某一去心邻域内有定义. 如果存在常数 $A$, 对于任意给定的正数 $\epsilon$ (不论它有多么小), 总存在正整数 $\delta$, 使得当 $x$ 满足不等式 $0\lt|x-x_0|\lt\delta$ 时, 对应的函数值 $f(x)$ 都满足不等式
```math
|f(x)-A|\lt\epsilon
```
那么常数 $A$ 就叫做函数 $f(x)$ 当 $x\to x_0$ 时的极限, 记作:
```math
\lim_{x\to x_0}f(x)=A\ \ 或\ \ f(x) \to A(当 x\to x_0)
```

#### 自变量趋于无穷大时函数的极限
**定义 2** 设函数 $f(x)$ 当 $|x|$ 大于某一正数时有定义. 如果存在常数 $A$, 对于任意给定的正数 $\epsilon$ (无论它有多么小), 总存在着正数 $X$, 使得当 $x$ 满足不等式 $|x|\gt X$ 时, 对应的函数值 $f(x)$ 都满足不等式:
```math
|f(x)-A|\lt \epsilon
```
那么常数 $A$ 就叫做函数 $f(x)$ 当 $x\to\infty$ 时的极限, 记作:
```math
\lim_{x\to\infty}f(x)=A\ \ 或\ \ f(x)\to A(当 x\to\infty)
```
定义2 可简单地表达为:
```math
\lim_{x\to\infty}f(x)=A\Leftrightarrow \forall\epsilon\lt 0,\exists X \gt 0, 当 |x|\gt X 时, 有 |f(x)-A|\lt\epsilon
```

### 函数极限的性质
**定理 1(函数极限的唯一性)** 如果 $\lim_{x\to x_0}f(x)$ 存在, 那么极限唯一.

**定理 2(函数极限的局部有界性)** 如果 $\lim_{x\to x_0}f(x)=A$, 那么存在常数 $M\gt 0$ 和 $\delta\gt 0$, 使得当 $0\lt |x-x_0|\lt \delta$ 时, 有 $f|x|\le M$.

**定理 3(函数极限的局部保号性)** 如果 $\displaystyle\lim_{x\to x_0}f(x)=A$, 其 $A\gt 0$(或 $A\lt 0$) 那么存在常数 $\delta \gt 0$, 使得当 $0\lt|x-x_0|\lt\delta$ 时, 有 $f(x)\gt 0$(或 $f(x)\lt 0$).

**定理 4(函数极限与数列极限的关系)** 如果极限 $\displaystyle\lim_{x\to x_0}f(x)$ 存在, $\{ x_n \}$ 为函数 $f(x)$ 的定义域内任一收敛于 $x_0$ 的数列, 且满足 $x_n \neq x_0 (n \in N_+)$ , 那么相应的函数值数列 $\{f(x_n)\}$ 必收敛, 且 $\displaystyle \lim_{x \to \infty}f(x_n) = \lim_{x \to x_0}f(x)$

## 无穷小与无穷大
### 无穷小
**定义 1** 如果函数 $f(x)$ 当 $x\to x_0$ (或 $x\to\infty$) 时的极限为0, 那么称函数 $f(x)$ 为 $x\to x_0$ (或 $x\to\infty$) 时的无穷小.

**定理 1** 在自变量的同一变化过程 $x\to x_0$ (或 $x\to\infty$) 中, 函数 $f(x)$ 具有极限 $A$ 的充分必要条件是: $f(x)=A+a$, 其中 $a$ 是无穷小.

### 无穷大
**定义 2** 设函数 $f(x)$ 在 $x_0$ 的某一去心邻域内有定义(或 $|x|$ 大于某一正数时有定义). 如果对于任意给定的正数 $M$ (无论它多么大), 总存在正数 $\delta$ (或正数 $X$), 只要 $x$ 适合不等式 $0\lt|x-x_0|\lt \delta$ ,对应的函数值 $f(x)$ 总满足不等式
```math
|f(x)|\gt M
```
那么称函数 $f(x)$ 是当 $x\to x_0$ (或 $x\to\infty$) 时的无穷大.

**定理 2** 在自变量的同一变化过程中, 如果 $f(x)$ 为无穷大, 那么 $\displaystyle\frac{1}{f(x)}$ 为去穷小; 反之, 如果 $f(x)$ 为无穷小, 且 $f(x)\neq 0$, 那么 $\displaystyle\frac{1}{f(x)}$ 为无穷大.

## 极限运算法则
**定理 1** 两个无穷小的和是无穷小.

**定理 2** 有界无穷小与无穷小的积是无穷小.

**推论 1** 常数与无穷小的乘积是无穷小.

**推论 2** 有限个无穷小的乘积是无穷小.

**定理 3** 如果 $\lim f(x)=A, \lim g(x)=B$, 那么
* $\lim[f(x)\pm g(x)]=\lim f(x) \pm \lim g(x)$
* $\lim[f(x)\cdot g(x)]=\lim f(x) \cdot \lim g(x)$
* 若又有 $B \neq 0$, 则
```math
\lim \frac{f(x)}{g(x)}=\frac{\lim f(x)}{\lim g(x)} = \frac{A}{B}
```

**推论 1** 如果 $\lim f(x)$ 存在, 而 $c$ 为常数, 那么
```math
\lim[cf(x)]=c\lim f(x)
```

**推论 2** 如果 $\lim f(x)$ 存在, 而 $n$ 是正整数, 那么
```math
\lim[f(x)]^n=[\lim f(x)]^n
```

**定理 4** 设有数列 $\{x_n\}$ 和 $\{y_n\}$. 如果
```math
\lim_{x\to\infty}x_n = A, \lim_{n\to\infty}y_n = B
```
那么:
* $\displaystyle \lim_{n\to\infty}x_n \pm y_n = A + B$
* $\displaystyle \lim_{n\to\infty}x_n \cdot y_n = A \cdot B$
* 当 $y_n\neq 0(n = 1,2,\cdots)$ 且 $B\neq 0$ 时, $\displaystyle\lim_{n\to\infty}\frac{x_n}{y_n} = \frac{A}{B}$

**定理 5** 如果 $\varphi(x)\ge\psi(x)$, 而 $\lim\varphi(x) = A, \lim\psi(x) = B$, 那么 $A\ge B$.

**定理 6(复合函数的极限运算法则)** 设函数 $y=f[g(x)]$ 是由函数 $u=g(x)$ 与 函数 $y=f(u)$ 复合而成, $f[g(x)]$ 在点 $x_0$ 的某去心邻域内有定义, 若 $\displaystyle\lim_{x\to x_0}g(x)=u_0, \lim_{u\to u_0}f(u) = A$,
且存在 $\delta_0 \gt 0$, 当 $x \in \mathring{U}(x_0,\delta_0)$ 时, 有 $g(x)\neq u_0$ 则
```math
\lim_{x\to x_0}f[g(x)] = \lim_{u\to u_0}f(u) = A
```

## 极限存在准则 两个重要极限
**准则 I** 如果数列 $\{x_n\}, \{y_n\}$ 及 $\{z_n\}$ 满足下列条件:
* 从某项起, 即 $\exists n_0 \in N_+$, 当 $n\gt n_0$ 时,有:
```math
y_n \le x_n \le z_n
```
* $\displaystyle\lim_{n\to\infty} y_n = a, \lim_{n\to\infty} x_n = a$

那么数列 $\{x_n\}$ 的极限存在, 且 $\lim_{n\to\infty}x_n = a$

**准则 I'** 如果
* 当 $x\in \mathring{U}(x_0,r)$ (或 $|x| \gt M$) 时,
```math
g(x) \le f(x) \le h(x)
```
* $\displaystyle\lim_{\substack{x\to x_0 \\ (x\to\infty)}}g(x) = A, \lim_{\substack{x\to x_0 \\ (x\to\infty)}}h(x) = A$

那么 $\displaystyle\lim_{\substack{x\to x_0 \\ (x\to\infty)}}f(x)$ 存在, 且等于 $A$

准则 I 及 准则 I' 称为 **夹逼准则**

**准则 II** 单调有界数列必有极限.

**准则 II'** 设函数 $f(x)$ 在点 $x_0$ 某个左邻域内单调并有界, 则 $f(x)$ 在 $x_0$ 的左极限 $f(x_0^-)$ 必定存在.

**柯西(Cauchy) 极限存在法则** 数列 $\{x_n\}$ 收敛的充分必要条件是: 对于任意给定的正整数 $\epsilon$, 存在正整数 $N$ 使得当 $m\gt N, n \gt N$ 时, 有
```math
|x_n - x_m| \le \epsilon
```

## 无穷小的比较
**定义**

如果 $\displaystyle\lim \frac{\beta}{\alpha} = 0$, 那么就说 $\beta$ 是比 $\alpha$ 的**高阶无穷小**, 记作 $\beta=o(\alpha)$

如果 $\displaystyle\lim \frac{\beta}{\alpha} = \infty$, 那么就说 $\beta$ 是比 $\alpha$ 的**低阶无穷小**;

如果 $\displaystyle\lim \frac{\beta}{\alpha} = c \neq 0$, 那么就说 $\beta$ 与 $\alpha$ 是**同阶无穷小**;

如果 $\displaystyle\lim \frac{\beta}{\alpha^k} = c \neq 0$, 那么就说 那么就说 $\beta$ 是关于 $\alpha$ 的**k阶无穷小**;

如果 $\displaystyle\lim \frac{\beta}{\alpha} = 1$, 那么就说 $\beta$ 与 $\alpha$ 是**等价无穷小**, 记作 $\alpha \sim \beta$;

**定理 1** $\beta$ 与 $\alpha$ 是等价无穷小的充分必要条件为
```math
\beta = \alpha + o(\alpha)
```

**定理 2** 设 $\alpha \sim \widetilde{a}, \beta \sim \widetilde{\beta}$, 且 $\displaystyle\frac{\widetilde{\beta}}{\widetilde{\alpha}}$ 存在, 则
```math
\lim \frac{\beta}{\alpha} = \lim \frac{\widetilde{\beta}}{\widetilde{\alpha}}
```

## 函数的连续性与间断点
### 函数的连续性
**定义** 设函数 $y = f(x)$ 在点 $x_0$ 的某一去心邻域内有定义, 如果
```math
\lim_{\Delta x\to 0}\Delta y = \lim_{\Delta x\to 0}[f(x_0+\Delta x)-f(x_0)] = 0
```
那么就称函数 $y = f(x)$ 在点 $x_0$ 连续.

设函数 $y = f(x)$ 在点 $x_0$ 的某一去心邻域内有定义, 如果
```math
\lim_{x\to x_0}f(x) = f(x_0)
```

定义用 " $\epsilon-\delta$ " 语言表达如下:  
$f(x)$ 在 $x_0$ 连续 $\Leftrightarrow \forall \epsilon \gt 0, \exists \delta \gt 0$ 当 $|x-x_0| \lt \delta$ 时, 有 $|f(x)-f(x_0)| \lt \epsilon$

如果 $\lim_{x\to x_0}f(x) = f(x_0^-)$ 存在, 且等于 $f(x_0)$, 即
```math
f(x_0^-) = f(x_0)
```
那么就说函数 $f(x)$ 在点 $x_0$ **左连续**. 如果 $\lim_{x\to x_0}f(x) = f(x_0^+)$ 存在, 且等于 $f(x_0)$, 即
```math
f(x_0^+) = f(x_0)
```
那么就说函数 $f(x)$ 在点 $x_0$ **右连续**.

在区间上每一点都连续的函数, 叫做**在该区间上的连续函数**, 或**函数在该区间上连续**.

### 函数的间断点
设函数 $y = f(x)$ 在点 $x_0$ 的某一去心邻域内有定义, 如果函数 $f(x)$ 有下列三种情况之一:
* 在 $x=x_0$ 没有定义
* 虽在 $x=x_0$ 有定义, 但 $\displaystyle\lim_{x\to x_0}f(x)$ 不存在
* 虽然在 $x=x_0$ 有定义, 且 $\displaystyle\lim_{x\to x_0}f(x)$ 存在, 但 $\displaystyle\lim_{x\to x_0}f(x) \neq f(x_0)$

那么 $f(x)$ 在点 $x_0$ 为不连续, 而点 $x_0$ 称为函数 $f(x)$ 的**不连续点**或**间断点**

左极限 $f(x_0^-)$ 与右极限 $f(x_0^+)$ 都都存在, 但不相等, 称 $x_0$ 是函数 $f(x_0)$ 的**第一类间断点**, 不是第一类间断点的任何间断点都称为 **第二类间断点**.

## 连续函数的运算与初等函数的连续性
### 连续函数的和/差/积/商的连续性

**定理 1** 设函数 $f(x)$ 和 $g(x)$ 在点 $x_0$ 连续, 则它们的和(差) $f\pm g$ / 积 $f\cdot g$ 及商 $\displaystyle\frac{f}{g}$ (当 $g(x_0) \neq 0$ 时)都在点 $x_0$ 连续.

**定理 2** 如果函数 $y=f(x)$ 在区间 $I_x$ 上单调增加(或单调减少)且连续, 那么它的反函数 $x=f^{-1}(y)$ 也在对应的区间 $I_y=\{y\mid y=f(x),x\in I_x\}$ 上单调增加(或单调减少)且连续.

**定理 3** 设函数 $y=f[g(x)]$ 由函数 $u=g(x)$ 与函数 $y=f(u)$ 复合而成, $\mathring{U}(x_0) \subset D_{f\cdot g}$. 若 $\displaystyle\lim_{x\to x_0}g(x)=u_0$, 而函数 $y=f(u)$ 在 $u=u_0$ 连续, 则
```math
\lim_{x\to x_0}f[g(x)] = \lim_{u\to u_0}f(u) = f(u_0)
```

**定理 4** 设函数 $y=f[g(x)]$ 由函数 $u=g(x)$ 与函数 $y=f(u)$ 复合而成, $\mathring{U}(x_0) \subset D_{f\cdot g}$. 若 $\displaystyle\lim_{x\to x_0}g(x)=u_0$, 而函数 $y=f(u)$ 在 $u=u_0$ 连续, 则复合函数 $y=f[g(x)]$ 在 $x=x_0$ 也连续.

## 初等函数的连续性
基本初等函数在它们的定义域内都是连续的.

一切函数在其定义区间内都是连续的.

## 闭区间上连续函数的性质
### 有界性与最大值最小值定理
**定理 1(有界性与最大值最小值定理)** 在闭区间上连续的函数在该区间上有界且一定能取得它的最大值和最小值.

### 零点定理与介值定理
如果 $x_0$ 使 $f(x_0) = 0$, 那么 $x_0$ 称为函数 $f(x)$ 的零点.

**定理 2(零点定理)** 设函数 $f(x)$ 在闭区间 $[a,b]$ 上连续, 且 $f(a)$ 与 $f(b)$ 异号(即 $f(a)\cdot f(b) \lt  0$), 则在开区间 $(a,b)$ 内至少有一点 $\xi$, 使
```math
f(\xi) = 0
```

**定理 3(介值定理)** 设函数 $f(x)$ 在闭区间 $[a,b]$ 上连续, 且在这区间的端点取不同的函数值
```math
f(a) = A\ \ \ 及\ \ \ f(b) = B
```
则对于 $A$ 与 $B$ 之间的任意一个数 $C$, 在开区间 $(a,b)$ 内至少一点 $\xi$, 使得
```math
f(\xi) = C (a \lt \xi \lt b)
```

**推论** 在闭区间 $[a,b]$ 上连续的函数 $f(x)$ 的值域为闭区间 $[m,M]$, 其中 $m$ 与 $M$ 依次为 $f(x)$ 在 $[a,b]$ 上的最小值与最大值.

### 一致连续性
**定义** 设函数 $f(x)$ 在区间 $I$ 上有定义. 如果对于任意给定的正整数 $\epsilon$, 总存在正数 $\delta$, 使得对于区间 $I$ 上的任意点 $x_1,x_2$, 当 $|x_1-x_2|\lt \delta$ 时, 有
```math
|f(x_1) - f(x_2)| \le \epsilon
```

那么称函数 $f(x)$ 在区间 $I$ 上一致连续.

**定理 4(一致连续性)** 如果函数 $f(x)$ 在闭区间 $[a,b]$ 上连续, 那么它在该区间上一致连续.

---

## 第二章 · 导数与微分

## 导数概念
### 引例
#### 直线运动加速度
时间 $t$, 位置 $s$, 有
```math
s = f(t)
```
平均速度:
```math
\frac{s-s_0}{t-t_0} = \frac{f(t) - f(t_0)}{t - t_0}
```
在 $t_0$ 时刻的速度:
```math
v = \lim_{t\to t_0}\frac{f(t) - f(t_0)}{t - t_0}
```

#### 切线问题
```math
k = \lim_{x\to x_0}\frac{f(x) - f(x_0)}{x-x_0}
```
$k$ 是切线的斜率.

### 导数的定义
#### 函数在一点处的导数与导函数
**定义** 设函数 $y=f(x)$ 在点 $x_0$ 的某个去心邻域内有定义, 当自变量 $x$ 在 $x_0$ 处取得增量 $\Delta x$ (点 $x_0+\Delta x$ 仍在该邻域内) 时, 相应地, 因变量取得增量 $\Delta y=f(x_0+\Delta x) - f(x_0)$; 如果 $\Delta y$ 与 $\Delta x$ 之比当 $\Delta \to 0$ 时的极限存在, 那么称函数 $y = f(x)$ 在 $x_0$ 处可导, 并称这个极限为函数 $y = f(x)$ 在点 $x_0$ 处的导数, 记为 $f'(x_0)$,即
```math
f'(x_0)=\lim_{\Delta x \to 0}\frac{\Delta y}{\Delta x} = \lim_{\Delta x \to 0}\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}
```
也可记作 $\displaystyle y'\mid_{x=x_0}, \frac{\mathrm{d}y}{\mathrm{d}x}\mid_{x=x_0}$ 或 $\frac{\mathrm{d}f(x)}{\mathrm{d}x}\mid_{x=x_0}$

#### 求导数函数举例
略

#### 单侧导数
根据函数 $f(x)$ 在点 $x_0$ 处的导数 $f'(x_0)$ 的定义, 导数
```math
f'(x_0) = \lim_{h\to0}\frac{f(x_0+h)-f(x_0)}{h}
```
是一个极限, 而极限存在的充分必要条件是左/右极限都存在且相等, 因此 $f'(x_0)$ 存在即 $f(x)$ 在点 $x_0$ 处可导的充分必要条件是左/右极限
```math
\lim_{h\to0^-}\frac{f(x_0+h)-f(x_0)}{h}\ \ \ 及\ \ \ \lim_{h\to0^+}\frac{f(x_0+h)-f(x_0)}{h}
```
都存在且相等. 这两个极限分别称为函数 $f(x)$ 在点 $x_0$ 处的**左导数** 和**右导数**, 记作 
```math
\displaystyle f_-'(x_0) = \lim_{h\to0^-}\frac{f(x_0+h)-f(x_0)}{h}
```
```math
\displaystyle f_+'(x_0) = \lim_{h\to0^+}\frac{f(x_0+h)-f(x_0)}{h}
```

左导数和右导数统称为单侧导数.

如果 $f(x)$ 在开区间 $(a,b)$ 内可导, 且 $f_+'(a)$ 及 $f_-'(b)$ 都存在, 那么说 $f(x)$ 在**闭区间** $[a,b]$ 上可导.

### 导数的几何意义
函数 $y=f(x)$ 在点 $x_0$ 处的导数 $f'(x_0)$ 在几何上表示曲线 $y = f(x)$ 在点 $M(x_0, f(x_0)$ 处的切线的斜率, 即:
```math
f'(x_0) = \tan \alpha
```
其中 $\alpha$ 是切线的倾角. 

切线方程为:
```math
y - y_0 = f'(x_0)(x-x_0)
```
法线方程为:
```math
y-y_0 = -\frac{1}{f'(x_0)}(x-x_0)
```

### 函数可导性与连续性的关系
设函数 $y=f(x)$ 在点 $x$ 处可导, 即
```math
\lim_{x\to 0}\frac{\Delta y}{\Delta x} = f'(x)
```
存在. 由具有极限的函数与无穷小的关系知道:
```math
\frac{\Delta y}{\Delta x} = f'(x) + \alpha
```
其中 $\alpha$ 为当 $\Delta x \to 0$ 似的无穷小. 上式两边同乘 $\Delta x$ 得
```math
\Delta y = f'(x)\Delta x + \alpha \Delta x
```
由此可见, 当 $\Delta x \to 0$ 时, $\Delta y \to 0$. 这就是说, 函数 $y=f(x)$ 在点 $x$ 处是连续的. 所以, 如果 $y=f(x)$ 在点 $x$ 处可导, 那么函数在该点必定连续.

另一方面, 一个函数在某点连续却不一定在该点可导.

## 函数的求导法则
### 函数的和/差/积/商的求导法则
**定理 1** 如果函数 $u=u(x)$ 及 $v=v(x)$ 都在点 $x$ 具有导数, 那么他们的和/差/积/商(除分母为零的点外)都在点 $x$ 具有导数, 且:
* $[u(x)\pm v(x)]' = u'(x)\pm v'(x)$
* $[u(x)v(x)]' = u'(x)v(x) + u(x)v'(x)$
* $\displaystyle\left[\frac{u(x)}{v(x)}\right]' = \frac{u'(x)v(x)-u(x)v'(x)}{v^2(x)} (v(x) \neq 0)$

定理 1 的扩展:
* $(u+v-w)' = u'+v'-w'$
* $(uvw)' = (uv)'w + (uv)w' = (u'v + uv')w + uvw'$ 即 $(uvw)'=u'vw+uv'w+uvw'$

### 反函数求导法则
**定理 2** 如果函数 $x=f(y)$ 在区间 $I_y$ 內单调, 可导, 且 $f'(y) \neq 0$, 那么它的反函数 $y=f^{-1}(x)$ 在区间 $I_x=\{x\mid x=f(y),y\in I_y\}$ 内也可导, 且
```math
[f^{-1}(x)]' = \frac{1}{f'(y)}\ \ \ 或\ \ \ \frac{\mathrm{d}y}{\mathrm{d}x} = \frac{1}{\frac{\mathrm{d}x}{\mathrm{d}y}}
```

### 复合函数求导法则
**定理 3** 如果 $u=g(x)$ 在点 $x$ 可导, 而 $y=f(u)$ 在点 $u=g(x)$ 可导, 那么复合函数 $y=f[g(x)]$ 在点 $x$ 可导, 且其导数为:
```math
\frac{\mathrm{d}y}{\mathrm{d}x} = f'(u)\cdot g'(x) \ \ \ 或\ \ \ \frac{\mathrm{d}y}{\mathrm{d}x} = \frac{\mathrm{d}y}{\mathrm{d}u} \cdot \frac{\mathrm{d}u}{\mathrm{d}x}
```

### 基本求导法则与求导公式
#### 常数和基本初等函数的导数公式
* $(C)' = 0$
* $(x^\mu)' = \mu x^{\mu - 1}$
* $(\sin x)' = \cos x$
* $(\cos x)' = -\sin x$
* $(\tan x)' = \sec^2 x$
* $(\cot x)' = -\csc^2 x$
* $(\sec x)' = \sec x \tan x$
* $(\csc x)' = -\csc x \cot x$
* $(a^x)' = a^x\ln a\ (a\gt 0, a\neq 1)$
* $(e^x)' = e^x$
* $(\log_ax)' = \frac{1}{x\ln a}\ (a\gt 0,a\neq 1)$
* $(\ln x)' = \frac{1}{x}$
* $(\arcsin x)' = \frac{1}{\sqrt{1-x^2}}$
* $(\arccos x)' = -\frac{1}{\sqrt{1-x^2}}$
* $(\arctan x)' = \frac{1}{1+x^2}$
* $(\mathrm{arccot}x)' = -\frac{1}{1+x^2}$

#### 函数的和/差/积/商的求导法则
设 $u=u(x), v=v(x)$ 都可导, 则
* $(u\pm v)' = u' \pm v'$
* $(Cu)' = Cu' (C是常数)$
* $(uv)' = u'v + uv'$
* $\displaystyle(\frac{u}{v}) = \frac{u'v-uv'}{v^2}\ (v\neq 0)$

#### 反函数求导法则
设函数 $x=f(y)$ 在区间 $I_y$ 內单调, 可导, 且 $f'(y) \neq 0$, 那么它的反函数 $y=f^{-1}(x)$ 在区间 $I_x=\{x\mid x=f(y),y\in I_y\}$ 内也可导, 且
```math
[f^{-1}(x)]' = \frac{1}{f'(y)}\ \ \ 或\ \ \ \frac{\mathrm{d}y}{\mathrm{d}x} = \frac{1}{\frac{\mathrm{d}x}{\mathrm{d}y}}
```

#### 复合函数求导法则
设 $y=f(u)$, 而 $u=g(x)$ 且 $f(u)$ 及 $g(x)$ 都可导, 则复合函数 $y=f[g(x)]$ 的导数为:
```math
\frac{\mathrm{d}y}{\mathrm{d}x} = \frac{\mathrm{d}y}{\mathrm{d}u} \cdot \frac{\mathrm{d}u}{\mathrm{d}x}\ \ \ 或\ \ \ \frac{\mathrm{d}y}{\mathrm{d}x} = f'(u)\cdot g'(x)
```

## 高阶导数
一般地, 函数 $y=f(x)$ 的导数 $y'=f'(x)$ 仍然是 $x$ 的函数. 我们把 $y'=f'(x)$ 的导数叫做函数 $y=f(x)$ 的**二阶导数**, 记作 $y''$ 或 $\displaystyle\frac{\mathrm{d}^2y}{\mathrm{d}x}$, 即:
```math
y'' = (y')'\ \ \ 或\ \ \ \frac{\mathrm{d}^2y}{\mathrm{d}x^2} = \frac{\mathrm{d}}{\mathrm{d}x}(\frac{\mathrm{d}y}{\mathrm{d}x})
```

相应地, 把 $y=f(x)$ 的导数 $y'=f'(x)$ 叫做函数的**一阶导数**.

类似的, 二阶导数的导数, 叫做**三阶导数**, 一般地, $(n-1)$ 阶导数的导数叫做 $n$ 阶导数, 分别记作
```math
y''',y^{(2)},\cdots,y^{(n)}
```
或
```math
\frac{\mathrm{d}^3y}{\mathrm{d}x^3},\frac{\mathrm{d}^4y}{\mathrm{d}x^4},\cdots,\frac{\mathrm{d}^ny}{\mathrm{d}x^n}
```
函数 $y=f(x)$ 有 $n$ 阶导数, 也常说成函数 $y=f(x)$ 为 **$n$ 阶可导**.

函数 $y=f(x)$ 在点 $x$ 处具有 $n$ 阶导数, 那么 $y=f(x)$ 在点 $x$ 的某一去心邻域内必定具有一切低于 $n$ 阶的导数. 二阶及二阶以上的导数统称为**高阶导数**

## 隐函数及有参数方程所确定的函数的导数  相关变化率
### 隐函数的导数
把一个隐函数化成显函数, 叫做隐函数的显化.
**例 1** 求由方程 $e^y+xy-e=0$ 所确定的隐函数的导数 $\displaystyle\frac{\mathrm{d}y}{\mathrm{d}x}$

**解** 我们把方程两边分别对 $x$ 求导数, 注意 $y=y(x)$. 方程两边对 $x$ 求导得:
```math
\frac{\mathrm{d}}{\mathrm{d}x}(e^y+xy-e)=e^y\frac{\mathrm{d}y}{\mathrm{d}x}+y+x\frac{\mathrm{d}y}{\mathrm{d}x}
```
方程右边对 $x$ 求导得:
```math
(0)'=0
```
由于等式两边对 $x$ 的导数相等, 所以:
```math
e^y\frac{\mathrm{d}y}{\mathrm{d}x}+y+x\frac{\mathrm{d}y}{\mathrm{d}x} = 0
```
从而
```math
\frac{\mathrm{d}y}{\mathrm{d}x}=-\frac{y}{x+e^y}\ \ \ (x+e^y\neq 0)
```

### 由参数方程所确定的函数的导数
一般地, 若参数方程
```math
\begin{cases}
x=\varphi(t) \\
y=\psi(t)
\end{cases}
```
确定 $y$ 与 $x$ 间的函数关系, 则称此函数关系所表达的函数为由上述参数方程所确定的函数.

根据复合函数的求导法则与反函数的求导法则有:
```math
\frac{\mathrm{d}y}{\mathrm{d}x}=\frac{\mathrm{d}y}{\mathrm{d}t}\cdot\frac{\mathrm{d}t}{\mathrm{d}x}=\frac{\mathrm{d}y}{\mathrm{d}t}\cdot\frac{1}{\frac{\mathrm{d}x}{\mathrm{d}t}}=\frac{\psi'(t)}{\varphi'(t)}
```
即
```math
\frac{\mathrm{d}y}{\mathrm{d}x}=\frac{\psi'(t)}{\varphi'(t)}
```
上式也可以写成:
```math
\frac{\mathrm{d}y}{\mathrm{d}x}=\frac{\frac{\mathrm{d}y}{\mathrm{d}t}}{\frac{\mathrm{d}x}{\mathrm{d}t}}
```
如果 $x=\varphi(t), y=\psi(t)$ 还是二阶可导的, 那么又可得到函数的二阶求导公式:
```math
\begin{aligned}
\frac{\mathrm{d}^2y}{\mathrm{d}x^2}&=\frac{\mathrm{d}}{\mathrm{d}x}\left(\frac{\mathrm{d}y}{\mathrm{d}x}\right)=\frac{\mathrm{d}}{\mathrm{d}x}\left(\frac{\psi'(t)}{\varphi'(t)}\right)\cdot\frac{\mathrm{d}t}{\mathrm{d}x} \\
&=\frac{\psi''(t)\varphi'(t)-\psi'(t)\varphi''(t)}{\varphi'^2(t)}\cdot\frac{1}{\varphi'(t)}
\end{aligned}
```
即
```math
\frac{\mathrm{d}^2y}{\mathrm{d}x^2}=\frac{\psi''(t)\varphi'(t)-\psi'(t)\varphi''(t)}{\varphi'^3(t)}
```

### 相关变化率
设 $x=x(t)$ 及 $y=y(t)$ 都是可导函数, 而变量 $x$ 与 $y$ 间存在某种关系, 从而变化率 $\displaystyle\frac{\mathrm{d}x}{\mathrm{d}t}$ 与 $\displaystyle\frac{\mathrm{d}y}{\mathrm{d}t}$ 间也存在一定关系. 这两个相互以来的变化率称为**相关变化率**. 

## 函数的微分
### 微分的定义
**定义** 设函数 $y=f(x)$ 在某区间内有定义, $x_0$ 及 $x_0+\Delta x$ 在这区间内, 如果函数的增量
```math
\Delta y = f(x_0 + \Delta x) - f(x_0)
```
可表示为:
```math
\Delta y = A\Delta x + o(\Delta x)
```
其中 $A$ 是不依赖于 $\Delta x$ 的常数, 那么城函数 $y=f(x)$ 在点 $x_0$ 是**可微**的. 而 $A\Delta x$ 叫做函数 $y=f(x)$ 在点 $x_0$ 相应于自变量 $\Delta x$ 的**微分**, 记作 $\mathrm{d}y$, 即
```math
\mathrm{d}y=A\Delta x
```

### 微分的几何意义
在直角坐标系中, 函数 $y=f(x)$ 的图形是一条曲线. 对于某一固定的 $x_0$ 值, 曲线上有一个确定点 $M(x_0,y_0)$, 当自变量 $x$ 有微小增量 $\Delta x$ 时, 就得到曲线上另一个点 $N(x_0+\Delta x, y_0+\Delta y)$, 可知:
```math
MQ=\Delta x
QN=\Delta y
```
过点 $M$ 做曲线的切线 $MT$ , 它的倾角为 $\alpha$, 则
```math
QP=MQ\cdot\tan\alpha=\Delta x\cdot f'(x_0)
```
即
```math
\mathrm{d}y=QP
```

### 基本初等函数的微分公式与微分运算法则
函数的微分公式:
```math
\mathrm{d}y=f'(x)\mathrm{d}x
```

#### 基本初等函数的微分公式
|导数公式|微分公式|
|-|-|
|$(x^\mu)'=\mu x^{\mu-1}$|$\mathrm{d}(x^u)=\mu x^{\mu-1}\mathrm{d}x$|
|$(\sin x)' = \cos x$|$\mathrm{d}(\sin x)=\cos x\mathrm{d}x$|
|$(\cos x)' = -\sin x$|$\mathrm{d}(\cos x)=-\sin x\mathrm{d}x$|
|$(\tan x)' = \sec^2 x$|$\mathrm{d}()=\sec^2x\mathrm{d}x$|
|$(\cot x)' = -\csc^2 x$|$\mathrm{d}()=-\csc^2\mathrm{d}x$|
|$(\sec x)' = \sec x \tan x$|$\mathrm{d}(\sec x)=\sec x\tan x\mathrm{d}x$|
|$(\csc x)' = -\csc x \cot x$|$\mathrm{d}(\csc x)=-\csc x\cot x\mathrm{d}x$|
|$(a^x)' = a^x\ln a\ (a\gt 0, a\neq 1)$|$\mathrm{d}(a^x)=a^x\ln a\mathrm{d}x\ \ (a\gt 0 且 a \neq 1)$|
|$(e^x)' = e^x$|$\mathrm{d}(e^x)=e^x\mathrm{d}x$|
|$(\log_ax)' = \frac{1}{x\ln a}\ (a\gt 0,a\neq 1)$|$\mathrm{d}(\log_a x)=\frac{1}{x\ln a}\mathrm{d}x\ \ (a\gt 0 且 a \neq 1)$|
|$(\ln x)' = \frac{1}{x}$|$\mathrm{d}(\ln x)=\frac{1}{x}\mathrm{d}x$|
|$(\arcsin x)' = \frac{1}{\sqrt{1-x^2}}$|$\mathrm{d}(\arcsin x)=\frac{1}{\sqrt{1-x^2}}\mathrm{d}x$|
|$(\arccos x)' = -\frac{1}{\sqrt{1-x^2}}$|$\mathrm{d}(\arccos x)=-\frac{1}{\sqrt{1-x^2}}\mathrm{d}x$|
|$(\arctan x)' = \frac{1}{1+x^2}$|$\mathrm{d}(\arctan x)=\frac{1}{1+x^2}\mathrm{d}x$|
|$(\mathrm{arccot}x)' = -\frac{1}{1+x^2}$|$\mathrm{d}(\mathrm{arccot}x)=-\frac{1}{1+x^2}\mathrm{d}x$|

#### 函数和/差/积商的微分法则
|函数和/差/积商的求导法则|函数和/差/积商的微分法则|
|-|-|
|$(u\pm v)' = u' \pm v'$|$\mathrm{d}(u\pm v)=\mathrm{d}u\pm \mathrm{d}v$|
|$(Cu)' = Cu' (C是常数)$|$\mathrm{d}(Cu)=C\mathrm{d}u$|
|$(uv)' = u'v + uv'$|$\mathrm{d}(uv)=v\mathrm{d}u+u\mathrm{d}v$|
|$\displaystyle(\frac{u}{v}) = \frac{u'v-uv'}{v^2}\ (v\neq 0)$|$\mathrm{d}\left(\frac{u}{v}\right)=\frac{v\mathrm{d}u-u\mathrm{d}v}{v^2}\ \ (v\neq 0)$|

#### 复合函数的微分法则
设 $y=f(u)$ 及 $u=g(x)$ 都可导, 则复合函数 $x=f[g(x)]$ 的微分为:
```math
dy=y', dx=f'(u)g'(x)\mathrm{d}x
```
由于 $g'(x)\mathrm{d}x=\mathrm{d}u$, 所以, 复合函数 $x=f[g(x)]$ 的微分公式可写成
```math
\mathrm{d}y=f'(u)\mathrm{d}u\ \ \ 或\ \ \ \mathrm{d}y=y'_u\mathrm{d}u
```
由此可见, 无论 $u$ 是自变量还是中间变量, 微分形式 $\mathrm{d}y=f'(u)\mathrm{d}u$ 保持不变. 这一性质称为**微分形式不变性**. 这性质表示, 当变换自变量时, 微分形式 $\mathrm{d}y=f'(u)\mathrm{d}u$ 并不改变.

### 微分在近似计算中的应用
#### 函数的近似计算
如果 $y=f(x)$ 在点 $x_0$ 处的导数 $f'(x_0)\neq0$, 且 $|\Delta x|$ 很小时, 我们有
```math
\Delta y \approx \mathrm{d}x=f'(x_0)\Delta x
```
这个式子也可以写为
```math
\Delta y=f(x_0+\Delta x)-f(x_0)\approx f'(x_0)\Delta x
```
或
```math
f(x_0+\Delta x)\approx f(x_0)+f'(x_0)(x-x_0)
```
如果 $f(x_0)$ 与 $f'(x_0)$ 都容易计算, 那么可以近似计算 $\Delta y$

#### 误差估计
根据带有误差的数据计算所得的结果也会有误差, 我们把它叫做**间接测量误差**

如果某个量的精确值为 $A$, 它的近似值为 $a$, 那么 $|A-a|$ 叫做 $a$ 的绝对差, 而绝对误差. 而绝对误差与 $|a|$ 的比值 $\displaystyle\frac{|A-a|}{a}$ 叫做 $a$ 的相对误差.

如果
```math
|A-a|\le \delta_A
```
那么 $\delta_A$ 叫做测量 $A$ 的**绝对误差限**, 而 $\displaystyle\frac{\delta_A}{|a|}$ 叫做测量 $A$ 的**相对误差限**.
---

## 第三章 · 微分中值定理与导数的应用

## 微分中值定理
### 罗尔定理
**费马引理** 设函数 $f(x)$ 在点 $x_0$ 的某邻域 $U(x_0)$ 内有定义, 并且在 $x_0$ 处可导, 如果对于任意的 $x\in U(x_0)$, 有
```math
f(x)\le f(x_0)\ \ \ (或 f(x) \ge f(x_0))
```
那么 $f'(x_0)=0$

**罗尔定理** 如果函数 $f(x)$ 满足
* 在闭区间 $[a,b]$ 上连续
* 在开区间 $(a,b)$ 内可导
* 在区间端点处的函数值相等, 即 $f(a) = f(b)$

那么在 $(a,b)$ 内至少有一点 $\xi (a\lt\xi\lt b)$, 使得 $f'(\xi)=0$

### 拉格朗日中值定理
**拉格朗日中值定理** 如果函数 $f(x)$ 满足
* 在闭区间 $[a,b]$ 上连续
* 在开区间 $(a,b)$ 内可导

那么在 $(a,b)$ 内至少有一点 $\xi (a\lt\xi\lt b)$, 使等式
```math
f(b)-f(a)=f'(\xi)(b-a)
```
成立.

**定理** 如果函数 $f(x)$ 在区间 $I$ 上连续, $I$ 内可导, 且导数为零, 那么 $f(x)$ 在区间 $I$ 上是一个常数.

### 柯西中值定理
**柯西中值定理** 如果函数 $f(x)$ 及 $F(x)$ 满足
* 在闭区间 $[a,b]$ 上连续
* 在开区间 $(a,b)$ 内可导
* 对于任一 $x\in(a,b), F'(x)\neq 0$
那么在 $(a,b)$ 内至少有一点 $\xi$, 使等式
```math
\frac{f(b)-f(a)}{F(b)-F(a)}=\frac{f'(\xi)}{F'(\xi)}
```
成立.

## 洛必达法则
**定理 1** 设
* 当 $x\to a$ 时, 函数 $f(x)$ 及 $F(x)$ 都趋于零
* 在点 $a$ 的某去心邻域内, $f'(x)$ 及 $F'(x)$ 都存在且 $F'(x)\neq 0$
* $\displaystyle\lim_{x\to a}\frac{f'(x)}{F'(x)}$ 存在 (或为无穷大)

则
```math
\lim_{x\to a}\frac{f(x)}{F(x)}=\lim_{x\to a}\frac{f'(x)}{F'(x)}
```
这种在一定条件下通过分子分母分别求导再求极限来确定未定式的值的方法称为**洛必达(L'Hospital)法则**

**定理 2** 设
* 当 $x\to\infty$ 时函数 $f(x)$ 及 $F(x)$ 都趋于零
* 当 $|x|\gt N$ 时, $f'(x)$ 与 $F'(x)$ 都存在, 且 $F'(x)\neq 0$
* $\displaystyle\lim_{x\to\infty}\frac{f'(x)}{F'(x)}$ 存在(或为无穷大)

则
```math
\lim_{x\to\infty}\frac{f(x)}{F(x)}=\lim_{x\to\infty}\frac{f'(x)}{F'(x)}
```

## 泰勒公式
**泰勒(Taylor)中值定理 1** 如果函数 $f(x)$ 在 $x_0$ 处具有 $n$ 阶导数, 那么存在 $x_0$ 的一个邻域, 对于该邻域内的任一 $x$ 有
```math
f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\cdots+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n + R_n(x)
```
其中
```math
R_n(x)=o((x-x_0)^n)
```

**泰勒(Taylor)中值定理 2** 如果函数 $f(x)$ 在 $x_0$ 的某个去心邻域 $U(x_0)$ 内具有 $(n_1)$ 阶导数, 那么对于任一 $x\in U(x_0)$, 有
```math
f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\cdots+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n + R_n(x)
```
其中
```math
R_n(x)=\frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}
```
这里 $\xi$ 是 $x_0$ 与 $x$ 之间的某个值.

## 函数的的单调性与曲线的凹凸性
### 函数单调性的判定法
**定理 1** 设函数 $y=f(x)$ 在 $[a,b]$ 上连续, 在 $(a,b)$ 内可导.
* 如果在 $(a,b)$ 内 $f'(x)\ge 0$, 且等号仅在有限多个点处成立, 那么函数 $y=f(x)$ 在 $[a,b]$ 上单调增加.
* 如果在 $(a,b)$ 内 $f'(x)\le 0$, 且等号仅在有限多个点处成立, 那么函数 $y=f(x)$ 在 $[a,b]$ 上单调减少.

### 曲线的凹凸与拐点
**定义** 设 $f(x)$ 在区间 $I$ 上连续, 如果对 $I$ 上任意两点 $x_1,x_2$ 恒有
```math
f\left(\frac{x_1+x_2}{2}\right) \lt \frac{f(x_1)+f(x_2)}{2}
```
那么称 $f(x)$ 在 $I$ 上的**图形是(向上)凹的(或凹弧)；如果恒有
```math
f\left(\frac{x_1+x_2}{2}\right) \gt \frac{f(x_1)+f(x_2)}{2}
```
那么称 $f(x)$ 在 $I$ 上的**图形是(向上)凸的(或凸弧)；

**定理 2** 设 $f(x)$ 在 $[a,b]$ 上连续, 在 $(a,b)$ 内具有一阶和二阶导数, 那么
* 若在 $(a,b)$ 内 $f''(x)\gt 0$, 则 $f(x)$ 在 $[a,b]$ 上的图形是凹的.
* 若在 $(a,b)$ 内 $f''(x)\lt 0$, 则 $f(x)$ 在 $[a,b]$ 上的图形是凸的.

## 函数的极值与最大值最小值
### 函数极值及其求法
**定义** 设函数 $f(x)$ 在点 $x_0$ 的某邻域 $U(x_0)$ 内有定义, 如果对于去心邻域 $\mathring{U}(x_0)$ 内的任一 $x$, 有
```math
f(x)\lt f(x_0)\ \ \ (或 f(x) \gt f(x_0))
```
那么称  $f(x_0)$ 是函数 $f(x)$ 的一个**极大值**(或**极小值**).

**定理 1(必要条件)** 设函数 $f(x)$ 在点 $x_0$ 处可导, 且在 $x_0$ 处取得极值, 则 $f'(x_0)=0$.

**定理 2(第一充分条件)** 设函数 $f(x)$ 在点 $x_0$ 处连续, 且在 $x_0$ 的某去心邻域 $\mathring{U}(x_0)$ 内可导.
* 若 $x\in(x_0-\delta, x_0))$ 时, $f'(x)\gt 0$, 而 $x\in (x_0,x_0+\delta)$ 时, $f'(x)\lt 0$, 则 $f(x)$ 在 $x_0$ 处取得极大值.
* 若 $x\in(x_0-\delta, x_0))$ 时, $f'(x)\lt 0$, 而 $x\in (x_0,x_0+\delta)$ 时, $f'(x)\gt 0$, 则 $f(x)$ 在 $x_0$ 处取得极小值.
* 若 $x\in(x_0-\delta, x_0))$ 时, $f'(x)$ 的符号保持不变, 则 $f(x)$ 在 $x_0$ 处没有极值.

**定理 3(第二充分条件)** 设函数 $f(x)$ 在点 $x_0$ 处有二阶导数且 $f'(x_0)=0, f''(x_0)\neq 0$ 则
* 当 $f''(x_0)\lt 0$ 时, 函数 $f(x)$ 在 $x_0$ 处取得极大值
* 当 $f''(x_0)\gt 0$ 时, 函数 $f(x)$ 在 $x_0$ 处取得极小值

### 最大值最小值问题
方法:
* 求出 $f(x)$ 在 $(a,b)$ 内的驻点及不可导点
* 计算 $f(x)$ 在上述驻点/不可导点处的函数值及 $f(a), f(b)$
* 比较上述各值的大小, 其中最大的便是 $f(x)$ 在 $[a,b]$ 上的最大值, 最小的便是  $f(x)$ 在 $[a,b]$ 上的最小值.

## 函数图形的描绘.
步骤:
* 确定函数 $y=f(x)$ 的定义域及函数所具有的某些特性(如奇偶性/周期性等), 并求处函数的一阶导数 $f'(x)$ 和二阶导数 $f''(x)$
* 求出一阶导数 $f'(x)$ 和二阶导数 $f''(x)$ 在函数定义域内的全部零点, 并求出函数 $f(x)$ 的间断点及 $f'(x)$ 和 $f''(x)$ 不存在的点, 用这些点把函数的定义域划分成几个部分区间.
* 确定这些部分区间内 $f'(x)$ 和 $f''(x)$ 符号, 并由此确定函数图形的升降/凹凸和拐点.
* 确定函数图形的水平, 铅直渐近线及其他变化趋势.
* 算出 $f'(x)$ 和 $f''(x)$ 的零点以及不存在的点对应的函数值, 定出图形上相应的点. 为了把图形描绘的准确些, 有时还需要补充一些点, 然后结合第三/四步中得到的结果, 联结这些点画出函数 $y=f(x)$ 的图形.

## 曲率
### 弧微分
设函数 $f(x)$ 在区间 $(a,b)$ 内具有连续导数, 在曲线 $y=f(x)$ 上取固定点 $M_0(x_0,y_0)$ 作为弧长的基点, 并规定依 $x$ 增大方向作为曲线的正向. 对曲线上任一点 $M(x,y)$, 规定有向弧段 $\overset{\frown}{M_0M}$ 的值 $s$ (简称弧 $s$)如下: $s$ 的绝对值等于这段弧的长度, 当有向弧段 $\overset{\frown}{M_0M}$ 的方向与曲线正向一致时 $s\gt 0$, 相反时 $s\lt 0$. 显然, 弧 $s$ 与 $x$ 存在函数关系 $s=s(x)$, 而且 $s(x)$ 是 $x$ 的单调增加函数. 下面求 $x(x)$ 的导数及微分.

设 $x,x+\Delta x$ 为 $(a,b)$ 内两个邻近的点, 它们在曲线 $y=f(x)$ 上对应的点为 $M,M'$, 并设对应于 $x$ 的增量为 $\Delta x$, 弧 $s$ 的增量为 $\Delta s$, 那么
```math
\Delta s = \overset{\frown}{M_0M'}-\overset{\frown}{M_0M}=\overset{\frown}{M_M'}
```
于是
```math
\begin{aligned}
\left(\frac{\Delta s}{\Delta x}\right)^2 &= \left(\frac{\overset{\frown}{MM'}}{\Delta x}\right)^2 = \left(\frac{\overset{\frown}{MM'}}{|MM'|}\right)^2\cdot\frac{|MM'|^2}{(\Delta x)^2} \\
&= \left(\frac{\overset{\frown}{MM'}}{|MM'|}\right)^2\cdot\frac{(\Delta x)^2+(\Delta y)^2}{(\Delta x)^2} \\
&= \left(\frac{\overset{\frown}{MM'}}{|MM'|}\right)\left[1+\left(\frac{\Delta y}{\Delta x}\right)^2\right] \\
\frac{\Delta s}{\Delta x} &= \pm\sqrt{\left(\frac{\overset{\frown}{MM'}}{|MM'|}\right)^2\cdot\left[1+\left(\frac{\Delta y}{\Delta x}\right)^2\right]}
\end{aligned}
```
令 $\Delta x \to 0$ 取极限, 由于 $\Delta x \to 0$ 时, $M' \to M$, 这时弧的长度与弦的长度之比的极限等于 1, 即
```math
\lim_{M'\to M}\frac{\overset{\frown}{MM'}}{|MM'|}=1
```
又
```math
\lim_{\Delta x \to 0}\frac{\Delta y}{\Delta x} = y'
```
因此得:
```math
\frac{\mathrm{d}s}{\mathrm{d}x}=\pm\sqrt{1+y'^2}
```
由于 $s=s(x)$ 是单调增加函数, 从而根号前应取正号, 于是有
```math
\mathrm{d}s = \sqrt{1+y'^2}\mathrm{d}x
```
这就是弧微分公式.

### 曲率及其计算公式
设曲线 $C$ 是光滑的, 在曲线 $C$ 上选定一点 $M_0$ 作为度量弧 $s$ 的基点. 设曲线上点 $M$ 对应于弧 $s$, 在点 $M$ 处切线的倾角为 $\alpha$ (这里假定曲线 $C$ 所在的平面上已设立了 $xOy$ 坐标系), 曲线上另外一点 $M'$ 对应于弧 $s+\Delta s$, 在点 $M'$ 出切线的倾角为 $\alpha + \Delta\alpha$, 则弧段 $\overset{\frown}{MM'}$ 的长度为 $|\Delta s|$, 当动点从 $M$ 移动到 $M'$ 时切线转过的角度为 $|\Delta\alpha|$.

我们用比值 $\displaystyle\frac{|\Delta\alpha|}{|\Delta s|}$, 即单位弧段上切线转过的角度大小来表达弧段 $\overset{\frown}{MM'}$ 弯曲程度, 把这比值叫做弧段 $\overset{\frown}{MM'}$ 的**平均曲率**, 并记作 $\overline{K}$, 即
```math
\overline{K}=\left|\frac{\Delta\alpha}{\Delta s}\right|
```
类似于从平均速度引进瞬时速度的方法, 当 $\Delta s \to 0$ 时(即 $M'\to M$ 时), 上述平均曲率的极限叫做曲线 $C$ 在点 $M$ 处的**曲率**, 记作 $K$, 即
```math
K=\lim_{\Delta s \to 0}\left|\frac{\Delta\alpha}{\Delta s}\right|
```
在 $\displaystyle\lim_{\Delta s \to 0}\frac{\Delta\alpha}{\Delta s}=\frac{\mathrm{d}\alpha}{\mathrm{d}s}$ 存在的条件下, $K$ 也可以表示为:
```math
K=\left|\frac{\mathrm{d}\alpha}{\mathrm{d}s}\right|
```
对于直线来说, 切线与直线本身重合, 当点沿直线移动时, 切线的倾角 $\alpha$ 不变, $\displaystyle\Delta \alpha = 0, \frac{\Delta \alpha}{\Delta s} = 0$, 从而 $\displaystyle K=\left|\frac{\mathrm{d}\alpha}{\mathrm{d}s}\right|=0$. 这就是说, 直线上任意点 $M$ 处的曲率都等于零. 这与我们直觉认识到的"直线不弯曲"一致.

设曲线的直角坐标方程是 $y=f(x)$, 其 $f(x)$ 具有二阶导数(这时 $f'(x)$ 连续, 从而曲线是光滑的). 因为 $\tan\alpha=y'$, 所以
```math
\begin{aligned}
\sec^2\alpha\frac{\mathrm{d}\alpha}{\mathrm{d}x}&=y'' \\
\frac{\mathrm{d}\alpha}{\mathrm{d}x}&=\frac{y''}{1+\tan^2\alpha}=\frac{y''}{1+y'^2}
\end{aligned}
```
于是
```math
\mathrm{d}\alpha=\frac{y''}{1+y'^2}\mathrm{d}x
```
由
```math
\mathrm{d}s=\sqrt{1+y'^2}\mathrm{d}x
```
从而根据曲率 $K$ 的表达式有:
```math
K=\frac{|y''|}{(1+y'^2)^{3/2}}
```
设曲线方程:
```math
\begin{cases}
x=\varphi(t) \\
y=\psi(t)
\end{cases}
```
给出, 则可利用由参数方程所确定的函数的求导法, 求出 $y'$, 及 $y''$, 带入上式得
```math
K=\frac{|\varphi(t)\psi''(t)-\varphi''(t)\psi'(t)|}{[\varphi'^2(t)+\psi'^2(t)]^{3/2}}
```

### 曲率圆与曲率半径

设曲线 $y=f(x)$ 在点 $M(x,y)$ 处的曲率为 $K(K\neq 0)$. 在点 $M$ 处的曲线的法线上, 在凹的一侧取一点 $D$, 使 $\displaystyle|DM|=\frac{1}{K}=\rho$. 以 $D$ 为圆心, $\rho$ 为半径作圆, 这个圆叫做曲线在点 $M$ 处的**曲率圆**, 曲率圆的圆心 $D$ 叫做曲线在点 $M$ 处的**曲率中心**, 曲率圆的半径 $\rho$ 叫做曲线在点 $M$ 处的**曲率半径**.

曲线在点 $M$ 处的曲率 $K(K\neq 0$ 与曲线在点 $M$ 处的曲率半径 $\rho$ 有如下关系:
```math
\rho=\frac{1}{K}, K=\frac{1}{\rho}
```
这就是说: 曲线上一点处的曲率圆半径与曲线在该点处的曲率互为倒数.

### 曲率中心的计算公式, 渐屈线与渐伸线
设已知曲线的方程是 $y=f(x)$, 且其二阶导数 $y''$ 在点 $x$ 不为零, 则曲线在对应点 $M(x,y)$ 的曲率中心 $D(\alpha, \beta)$ 的坐标为:
```math
\begin{cases}
\alpha &= x-\frac{y'(1+y'^2)}{y''}\\
\beta &= y+\frac{1+y'^2}{y''}
\end{cases}
```
这是因为, 曲线 $y=f(x)$ 在 $M(x,y)$ 的曲率圆方程为:
```math
(\xi-\alpha)^2+(\eta-\beta)^2=\rho^2
```
其中 $\xi,\eta$ 是曲率圆上的动点坐标, 且
```math
\rho^2=\frac{1}{K^2}=\frac{(1+y'^2)^3}{y''^2}
```
因为点 $M$ 在曲率圆上, 所以
```math
(x-\alpha)^2+(y-\beta)^2=\rho^2
```
又因为曲线在点 $M$ 的切线与曲率圆的半径 $DM$ 互相垂直, 所以
```math
y'=-\frac{x-\alpha}{y-\beta}
```
消去 $x-\alpha$ 解出
```math
(y-\beta)^2=\frac{\rho^2}{1+y'^2}=\frac{(1+y'^2)}{y''^2}
```
由于当 $y''\gt 0$ 时曲线为凹弧, $y=\beta \lt 0$; 当 $y''\lt 0$ 时曲线为凸弧, $y=\beta \gt 0$. 总之 $y''$ 与 $y-\beta$ 异号. 因此取上式两边的平方根得:
```math
y-\beta=\frac{1+y'^2}{y''}
```
又
```math
x-\alpha=-y'(y-\beta)=\frac{y'(1+y'^2)}{y''}
```
从而上述坐标公式.

当点 $(x,f(x))$ 沿曲线 $C$ 移动是, 相应的曲率中心 $D$ 的轨迹曲线 $G$ 成为曲线 $C$ 的**渐屈线**, 而曲线 $C$ 成为曲线 $G$ 的**渐伸线**. 所以曲线 $y=f(x)$ 的渐屈线的参数方程为:
```math
\begin{cases}
\alpha=x-\frac{y'(1+y'^2)}{y''} \\
\beta=y+\frac{1+y'^2}{y''}
\end{cases}
```
其中 $y=f(x), y'=f'(x),y''=f''(x)$, $x$ 为参数, 直角坐标系 $\alpha O \beta$ 与 $xOy$ 坐标系重合.

## 方程的近似解
### 二分法
设 $f(x)$ 在区间 $[a,b]$ 上连续, $f(a)\cdot f(b)\lt 0$, 且方程 $f(x)=0$ 在 $(a,b)$ 内仅有一个实根 $\xi$, 于是 $[a,b]$ 即是这个根的一个隔离区间.

取 $[a,b]$ 的中点 $\displaystyle\xi_1=\frac{a+b}{2}$ , 计算 $f(\xi_1)$

如果 $f(\xi_1)=0$, 那么 $\xi=\xi_1$

如果 $f(\xi_1)$ 与 $f(a)$ 同号, 那么取 $a_1=\xi_1, b_1=b$, 由 $f(a_1)\cdot f(b_1)\lt 0$, 即知 $a_1 \lt \xi_1 \lt b_1$, 且 $\displaystyle b_1=a_1=\frac{1}{2}(b-a)$

如果 $f(\xi_1)$ 与 $f(b)$ 同号, 那么取 $a_1=a, b_1=\xi_1$, 也有 $a_1 \lt \xi_1 \lt b_1$, 及 $\displaystyle b_1=a_1=\frac{1}{2}(b-a)$

总之, 当 $\xi \neq \xi_1$ 时, 可求得 $a_1 \lt \xi_1 \lt b_1$, 且 $\displaystyle b_1=a_1=\frac{1}{2}(b-a)$

以 $[a_1,b_1]$ 作为新的隔离区间, 重复上述做法, 当 $\xi\neq\xi_2=\frac{1}{2}(a_1+b_1)$ 时, 可求得 $\displaystyle a_1\lt\xi\lt b_2$, 且 $\displaystyle b_2-a_2=\frac{1}{2^2}(b-a)$

如此重复 $n$ 次, 可求得 $a_b\lt\xi\lt b_n$, 且 $\displaystyle b_n-a_n=\frac{1}{2^n}(b-a)$. 由此可知, 如果以 $a_n$ 或 $b_n$ 作为 $\xi$ 的近似值, 那么其误差小于 $\displaystyle\frac{1}{2^n}(b-a)$

### 切线法
设 $f(x)$ 在区间 $[a,b]$ 上有二阶导数, $f(a)\cdot f(b)\lt 0$ 且 $f'(x)$ 及 $f''(x)$ 在 $[a,b]$ 上保持定号. 在上述条件下, 方程 $f(x)=0$ 在 $(a,b)$ 内有唯一的实根 $\xi$, $[a,b]$ 为根的一个隔离区间. 此时 $y=f(x)$ 在 $[a,b]$ 上的图形 $\overset{\frown}{AB}$ 只有四种不同情形.

以 $f(a)\lt 0, f(b) \gt 0, f'(x)\gt 0, f''(x) \gt 0$ 情形为例进行讨论. 此时因为 $f(b)$ 与 $f''(x)$ 同号, 所以令 $x_0=b$ 在端点 $(x_0,f(x_0))$ 处做切线, 切线的方程为:
```math
y-f(x_0)=f'(x_0)(x-x_0)
```
令 $y=0$, 从上式中解出 $x$, 就得到切线与 $x$ 轴的交点的横坐标为:
```math
x_1=x_0-\frac{f(x_0)}{f'(x_0)}
```
它比 $x_0$ 更接近方程的根 $\xi$

再在点 $(x_1, f(x_1))$ 处做切线, 可得近似值 $x_2$, 如此继续, 一般地, 在点 $(x_n,f(x_n))$ 处做切线, 得根的近似值:
```math
x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}
```

如果 $f(a)$ 与 $f''(x)$ 同号, 那么切线在端点 $(a,f(a))$ 处, 可记 $x_0=a$, 扔按公式计算切线与 $x$ 轴交点的横坐标.

### 割线法
利用切线法计需要计算函数的导数, 当 $f(x)$ 比较复杂时, 计算 $f'(x)$ 可能有困难. 这时可以考虑用 
```math
\frac{f(x_n)-f(x_{n-1})}{x_n-x_{n-1}}
```
来近似替代切线法中的 $f'(x_n)$, 这时的迭代公式成为
```math
x_{n+1}=x_n-\frac{x_n-x_{n-1}}{f(x_n)-f(x_{n-1})}\cdot f(x_n)
```
其中 $x_0, x_1$ 为初始值. 这个方法叫做**割线法**或**截弦法**
---

## 第四章 · 不定积分

## 不定积分的概念与性质
### 原函数与不定积分概念
**定义 1** 如果在区间 $I$ 上, 可导函数 $F(x)$ 的到函数为 $f(x)$, 即对任一 $x\in I$ 都有:
```math
F'(x)=f(x) \ \ \ 或\ \ \ \mathrm{d}F(x)=f(x)\mathrm{d}x
```
那么函数 $F(x)$ 就称为 $f(x)$ (或 $f(x)\mathrm{d}x$) 在区间 $I$ 上的一个**原函数**

**原函数存在定理** 如果函数 $f(x)$ 在区间 $I$ 上连续, 那么在区间 $I$ 上存在可导函数 $F(x)$, 使对于任一 $x\in I$ 都有 
```math
F'(x)=f(x)
```
简单的说就是: **连续函数一定有原函数**.

还要说明两点:

**第一** 如果 $f(x)$ 在区间 $I$ 上有原函数, 即有一个函数 $F(x)$ , 是对于任一 $x\in I$ 都有 $F'(x)=f(x)$, 那么对任何常数 $C$, 显然也有
```math
[F(x)+C]'=f(x)
```
即对于任何常数 $C$, 函数 $F(x)+C$ 也是 $f(x)$ 的原函数, 这说明, 如果 $f(x)$ 有一个原函数, 那么 $f(x)$ 就有无限多个原函数.

**第二**, 如果在区间 $I$ 上 $F(x)$ 是 $f(x)$ 的一个原函数, 那么 $f(x)$ 的其他原函数与 $F(x)$ 有什么关系?

设 $\Phi(x)$ 是 $f(x)$ 的另一个原函数, 即对任一 $x\in I$ 有
```math
\Phi'(x)=f(x)
```
于是
```math
[\Phi(x)-F(x)]'=\Phi'(x)-F'(x)=f(x)=f(x)=0
```
在一个区间上导数恒为零的函数必为常数, 所以
```math
\Phi(x)-F(x)=C_0\ \ \ (C_0为某个常数)
```

这表明 $\Phi(x)$ 与 $F(x)$ 只差一个常数. 因此, 当 $C$ 为任意的常数时, 表达式
```math
F(x) + C
```
就可以表示 $f(x)$ 的任意一个原函数.

**定义 2** 在区间 $I$ 上, 函数 $f(x)$ 的带有任意常数项的原函数称为 $f(x)$ (或 $f(x)\mathrm{d}x$) 在区间 $I$ 上的**不定积分**, 记作
```math
\int f(x)\mathrm{d}x
```
其中记号 $\int$ 称为**积分符号**, $f(x)$ 称为**被积函数**, $f(x)\mathrm{d}x$ 称为**被积表达式**, $x$称为**积分变量**.

由此定义及前面的说明可知, 如果 $F(x)$ 是 $f(x)$ 在区间 $I$ 上的一个原函数, 那么 $F(x)+C$ 就是 $f(x)$ 的不定积分, 即
```math
\int f(x)\mathrm{d}x=F(x)+C
```
因而不定积分 $\displaystyle\int f(x)\mathrm{d}x$ 可以表示 $f(x)$ 的任意一个原函数.

### 基本积分表
基本积分表
$$
\int k\,\mathrm{d}x=kx+C \quad (k\text{是常数})
$$

$$
\int x^\mu\,\mathrm{d}x=\frac{x^{\mu+1}}{\mu+1} \quad (\mu\neq -1)
$$

$$
\int \frac{\mathrm{d}x}{x}=\ln|x|+C
$$

$$
\int \frac{\mathrm{d}x}{1+x^2}=\arctan x+C
$$

$$
\int \frac{\mathrm{d}x}{\sqrt{1-x^2}}=\arcsin x+C
$$

$$
\int \cos x\,\mathrm{d}x=\sin x+C
$$

$$
\int \sin x\,\mathrm{d}x=-\cos x+C
$$

$$
\int \frac{\mathrm{d}x}{\cos^2 x}=\tan x+C
$$

$$
\int \frac{\mathrm{d}x}{\sin^2 x}=-\cot x+C
$$

$$
\int \frac{\sin x}{\cos^2 x}\,\mathrm{d}x=\frac{1}{\cos x}+C
$$

$$
\int \frac{\cos x}{\sin^2 x}\,\mathrm{d}x=-\frac{1}{\sin x}+C
$$

$$
\int e^x\,\mathrm{d}x=e^x+C
$$

$$
\int a^x\,\mathrm{d}x=\frac{a^x}{\ln a}+C
$$

以上十三种基本积分是求解不定积分的基础, **必须熟记**. 

### 不定积分的性质
**性质 1** 设函数 $f(x)$ 及 $g(x)$ 的原函数存在, 则
```math
\int[f(x)+g(x)]\mathrm{d}x=\int f(x)\mathrm{d}x+\int g(x)\mathrm{d}x
```

**性质 2** 设函数 $f(x)$ 的原函数存在, $k$ 为非零常数, 则
```math
\int kf(x)\mathrm{d}x=k\int f(x)\mathrm{d}x
```

## 换元积分法
### 第一类积分法
设 $f(u)$ 具有原函数 $F(u)$, 即
```math
F'(u)=f(u),\ \int f(u)\mathrm{d}u=F(u)+C
```
如果 $u$ 是中间变量: $u=\varphi(x)$, 且设 $\varphi(x)$ 可微, 那么根据复合函数微分法, 有
```math
\mathrm{d}F[\varphi(x)]=f[\varphi(x)]\varphi'(x)\mathrm{d}x
```
从而根据不定积分的定义得
```math
\int f[\varphi(x)]\varphi'(x)\mathrm{d}x=F[\varphi(x)] +C=\left[\int f(u)\mathrm{d}u\right]_{u=\varphi(x)}
```
于是有下述定理

**定理 1** 设 $f(u)$ 具有原函数, $u=\varphi(x)$ 可导, 则有换元公式
```math
\int f[\varphi(x)]\varphi'(x)\mathrm{d}x=\left[\int f(u)\mathrm{d}u\right]_{u=\varphi(x)}
```

### 第二类换元法
**定理 2** 设 $x=\psi(t)$ 是单调的可导函数, 并且 $\psi'(t)\neq 0$. 有设 $f[\psi(t)]\psi'(t)$ 具有原函数, 则有换元公式
```math
\int f(x)\mathrm{d}x=\left[\int f[\psi(t)]\psi'(t)\mathrm{d}t\right]_{t=\psi^{-1}(x)}
```
其中 $\psi^{-1}(x)$ 是 $x=\psi(t)$ 的反函数.

双曲积分公式
```math
\begin{aligned}
\int \sh x\,\mathrm{d}x&=\ch x+C \\
\int \ch x\,\mathrm{d}x&=\sh x+C
\end{aligned}
```

额外的几个积分公式
```math
\begin{aligned}
\int \tan x\,\mathrm{d}x&=-\ln|\cos x|+C \\
\int \cot x\,\mathrm{d}x&=\ln|\sin x|+C \\
\int \sec x\,\mathrm{d}x&=\ln|\sec x+\tan x|+C \\
\int \csc x\,\mathrm{d}x&=\ln|\csc x-\cot x|+C \\
\int \frac{\mathrm{d}x}{a^2+x^2}&=\frac{1}{a}\arctan \frac{x}{a}+C \\
\int \frac{\mathrm{d}x}{x^2+a^2}&=\frac{1}{a}\ln\left|\frac{x-a}{x+a}\right|+C \\
\int \frac{\mathrm{d}x}{\sqrt{a^2-x^2}}&=\arcsin\frac{x}{a}+C \\
\int \frac{\mathrm{d}x}{\sqrt{x^2+a^2}}&=\ln(x+\sqrt{x^2+a^2})+C \\
\int \frac{\mathrm{d}x}{\sqrt{x^2-a^2}}&=\ln|x+\sqrt{x^2-a^2}|+C
\end{aligned}
```

## 分布积分法
设函数 $u=u(x)$ 及 $v=v(x)$ 具有连续导数, 则两个函数乘积的导数公式为
```math
(uv)'=u'v+uv'
```
移项, 得
```math
uv'=(uv)'-u'v
```
对这个等式两边求不定积分, 得
```math
\int uv'\mathrm{d}x=uv-\int u'v\mathrm{d}x
```
上述公式称为**分部积分公式**. 简便起见, 可以写成:
```math
\int u\mathrm{d}v=uv-\int v\mathrm{d}u
```

## 有理函数的积分
### 有理函数的积分
两个多项式的商 $\displaystyle\frac{P(x)}{Q(x)}$ 称为**有理函数**. 又称 **有理分式**. 当分子多项式 $P(x)$ 的次数小于分母多项式 $Q(x)$ 的次数时, 称这有理函数为 **真分式**, 否则称为**假分式**.

利用多项式的除法, 总可以将一个假分式化成一个多项式和与一个真分式之和的形式.

对于真分式 $\displaystyle\frac{P(x)}{Q(x)}$, 如果分母可分解为两个多项式的乘积:
```math
Q(x)=Q_1(x)Q_2(x)
```
且 $Q_1(x)$ 与 $Q_2(x)$ 没有共因式, 那么它可拆成两个真分式之和
```math
\frac{P(x)}{Q(x)}=\frac{P_1(x)}{Q_1(x)}+\frac{P_2(x)}{Q_2(x)}
```
上述步骤成为把真分式化成部分分式之和.

### 可化为有理函数的积分
略

## 积分表的使用
往往把常用的积分公式汇集成表, 这种表叫做**积分表**
---

## 第五章 · 定积分

## 定积分的概念与性质
### 定积分问题举例
#### 曲边梯形的面积
设 $y=f(x)$ 在区间 $[a,b]$ 上非负/连续. 由直线 $x=a,x=b,y=0$ 及曲线 $y=f(x)$ 所围成的图形称为**曲边梯形**, 其中曲线弧称为**曲边**.

在区间 $[a,b]$ 中任意插入若干个分点
```math
a=x_0 \lt x_1 \lt x_2 \lt \cdots \lt x_{n-1} \lt x_n = b
```
把 $[a,b]$ 分成 $n$ 个小区间
```math
[x_0,x_1],[x_1,x_2],\cdots,[x_{n-1},x_n]
```
它们的长度依次为:
```math
\Delta x_1 = x_1-x_0, \Delta x_2=x_2-x_1,\cdots,\Delta x_n=x_n-x_{n-1}
```
记 $\lambda=max\{\Delta x_1,\Delta x_2,\cdots,\Delta x_n\}$, 所求曲边梯形面积 $A$ 的近似值, 即:
```math
A\approx f(\xi_1)\Delta x_1+f(\xi_2)\Delta x_2+\cdots+f(\xi_n)\Delta x_n=\sum_{i=1}^n f(\xi_i)\Delta x_i
```
得曲边梯形的面积
```math
A=\lim_{\lambda\to 0}\sum_{i=1}^n f(\xi_i)\Delta x_i
```

#### 变速直线运动的路程
在时间间隔 $[T_1,T_2]$ 内任意插入若干个分点
```math
T_1=t_0\lt t_1 \lt t_2 \lt \cdots \lt t_{n-1} \lt t_n=T_2
```
把 $[T_1,T_2]$ 分成 $n$ 个小时间段
```math
[t_0,t_1],[t_1,t_2],\cdots,[t_{n-1},t_n]
```
每个小时段时间的长度一次为:
```math
\Delta t_1 = t_1-t_0, \Delta t_2=t_2-t_1,\cdots,\Delta t_n=t_n-t_{n-1}
```
相应地, 在各段时间内物体经过的路程依次为
```math
\Delta s_1,\Delta s_2,\cdots,\Delta s_n
```
部分路程 $\Delta s_i$ 的近似值:
```math
\Delta s_i\approx v(\tau_i)\Delta t_i\ \ (i=1,2,\cdots,n)
```
变速直线运动路程 $s$ 的近似值为:
```math
s\approx v(\tau_1)\Delta t_1 + v(\tau_2)\Delta t_2+\cdots+v(\tau_n)\Delta t_n=\sum_{i=1}^n\Delta t_i
```
记 $\lambda=max\{\Delta t_1,\Delta t_,\cdots,\Delta t_n\}$, 当 $\lambda\to 0$ 时, 取上述和式的极限, 即得:
```math
s=\lim_{\lambda\to 0}\sum_{i=1}^nv(\tau_i)\Delta t_i
```

### 积分的定义
对于面积和路程, 归结为:
```math
\begin{aligned}
\text{面积}A&=\lim_{\lambda\to 0}\sum_{i=1}^n f(\xi_i)\Delta x_i \\
\text{路程}s&=\lim_{\lambda\to 0}\sum_{i=1}^n v(\tau_i)\Delta t_i
\end{aligned}
```

**定义** 设函数 $f(x)$ 在 $[a,b]$ 上有界, 在 $[a,b]$ 中任意插入若干个分点
```math
a=x_0\lt x_1 \lt x_2 \lt \cdots \lt x_{n-1} \lt x_n = b
```
把 $[a,b]$ 分成 $n$ 个小区间
```math
[x_0,x_1],[x_1,x_2],\cdots,[x_{n-1},x_n]
```
各个小区间的长度依次为:
```math
\Delta x_1 = x_1-x_0, \Delta x_2=x_2-x_1,\cdots,\Delta x_n=x_n-x_{n-1}
```
在每个小区间 $[x_{i-1}, x_i]$ 上任取一点 $\xi(x_{i-1}\le\xi_i\le x_i)$, 作函数值 $f(\xi_i)$ 与小区间长度 $\Delta x_i$ 的乘积 $f(\xi_i)\Delta x_i(i=1,2,\cdots,n)$, 并作出和
```math
S=\sum_{i=1}^n f(\xi_i)\Delta x_i
```
记 $\lambda=\mathrm{max}\{\Delta x_1,\Delta x_2,\cdots,\Delta x_n\}$, 如果当 $\lambda\to 0$ 时, 这和的极限总存在, 且与闭区间 $[a,b]$ 的分法及点 $\xi_i$ 的取法无关, 那么称这个极限 $I$ 为函数 $f(x)$ 在区间 $[a,b]$ 上的**定积分**(简称**积分**), 记作 $\displaystyle\int_a^b f(x)\mathrm{d}x$, 即:
```math
\int_a^b f(x)\mathrm{d}x=I=\lim_{\lambda\to 0}\sum_{i=1}^n f(\xi_i)\Delta x_i
```
其中 $f(x)$ 叫做**被积函数**, $f(x)\mathrm{d}x$ 叫做**被积表达式**, $x$ 叫**积分变量**, $a$ 叫做**积分下线**, $b$ 叫做**积分上限**, $[a,b]$ 叫做**积分区间**.
