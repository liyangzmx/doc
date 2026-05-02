# 基本概念
## 随机实验
确定性现象: 在一定条件下必然发生

统计规律性: 大量重复实验或观察中所所呈现出的固有规律性

随机现象: 在个别实验中其结果呈现出不确定性, 在大量重复实验中其结果又有规律性的现象

随机实验特点:
* 可以在相同的条件下重复地进行
* 每次实验的可能结果不止一个, 并且实现明确实验所有的可能结果
* 进行一次实验之前不能确定哪一个结果会出现

## 样本空间
样本空间: 将随机实验 $E$ 的所有可能结果组成的集合, 记为 $S$ 

样本点: 样本空间的元素, 即 $E$ 的每个结果

### 随机事件
随机事件: 试验 $E$ 的样本空间 $S$ 的子集为 $E$ 的随机事件, 简称**事件**

事件发生: 在每次实验中, 当且仅当这一子集中的一个样本点出现

基本事件: 又一个样本点组成的单点集

必然事件: 样本空间 $S$ 包含所有的样本点, 它是 $S$ 自身的子集, 在每次实验中它总是发生的.

不可能事件: 空集 $\emptyset$ 不包含任何样本点, 它作为样本空间的子集, 它在每次实验中都不发生

### 事件间的关系与事件的运算
设实验 $E$ 的样本空间为 $S$ , 而 $A, B, A_k(k = 1, 2, \ldots)$ 是 $S$ 的子集:
1. 若 $A \subset B$ 则称事件 $B$ 包含事件 $A$ , 这指的是事件  $A$ 发生必导致事件 $B$ 发生. 若 $A \subset B$ 且 $B \subset A$, 即 $A = B$, 则称事件 $A$ 与事件 $B$ 相等
2. 事件 $A \cup B = {x|x \in A 且 x \in B}$ 称为事件 $A$ 与事件 $B$ 的**和事件**. 当且仅当  $A,B$  中至少有一个发生时, 事件 $A \cup B$ 发生. 类似的 $\displaystyle\bigcup\limits_{k=1}^{n}A_k$ 为 $n$ 个事件 $A_1,  A_2, \ldots, A_n$  的和事件, 称 $\displaystyle\bigcup\limits_{k=1}^{n}A_k$ 为可列个事件 $A_1, A_2, \ldots$ 的和事件.
3. 事件 $A \cap B = {x|x \in A 且 x \in B}$ 成为事件 $A$ 与事件 $B$ 的 **积事件**. 当且仅当  $A,B$  同时发生时, 事件 $A \cap B$发生. $A \cap B$ 也记作 $AB$, 类似地称 $\displaystyle\bigcap\limits_{k=1}^{n}A_k$ 为事件 $A_1,  A_2, \ldots, A_n$ 的积事件, 称 $\displaystyle\bigcap\limits_{k=1}^{n}A_k$ 为可列个事件 $A_1, A_2, \ldots$ 的积事件.
4. 事件 $A-B={x|x \in A 且 x \notin B}$ 称为事件 $A$ 与事件 $B$ 的**差事件**, 当且仅当 $A$ 发生,  $B$ 不发生时事件 $A-B$ 发生.
5. 若 $A \cap B = \emptyset$, 则称事件  $A$ 与 $B$ 是**互不相容**的, 或**互斥**的, 这指的是事件 $A$ 与事件 $B$ 不可能同时发生. 基本事件是两两互不相容的.
6. 若 $A \cup B = S 且 A \cap B = \emptyset$, 则称事件 $A$ 与事件 $B$ 互为**逆事件**, 又称事件 $A$ 与事件 $B$ 是**对立事件**. 这指的是对每次实验而言, 事件  $A,B$  中必有一个发生, 且仅有一个发生.  $A$ 的对立事件记为 $\overline{A}, \overline{A} = S - A$

运算规律
* 交换律: $A \cup B = B \cup A$, $A \cap B = B \cap A$
* 结合律:
  * $A \cup (B \cup C) = (A \cup B) \cup C$
  * $A \cap (B \cap C) = (A \cap B) \cap C$
* 分配律
  * $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
  * $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$
* 德摩根律: $\overline{A \cup B} = \overline{A} \cap \overline{B}$

## 频率与概率
### 频率
定义: 在相同的条件下, 进行了 $n$ 次实验, 在这 $n$ 次实验中, 事件 $A$ 发生的次数 $n_A$ 称为事件 $A$ 发生的**频数**. 比值 $n_a / n$ 成为事件A发生的**频率**, 并记为 $f_n(A)$.

由定义, 易见频率具有下述基本性质:
1. $0 \le f_n(A) \le 1$
2. $f_n(S) = 1$
3. 若 $A_1, A_2, \ldots, A_k$ 是两两不相容的事件, 则:  
$$
f_n(A_1 \cup A_2 \cup \ldots \cup A_k) = f_n(A_1) = f_n(A_2) + \ldots + f_n(A_k)
$$

### 概率
定义: 设 $E$ 是随机实验,  $S$ 是它的样本空间, 对于 $E$ 的每一个事件 $A$ 赋予一个实数, 记为 $P(A)$, 称为事件 $A$ 的**概率**, 如果集合函数 $P(\cdot)$ 满足下列条件:
1. 非负性: 对于每一个事件 $A$ , 有 $P(A)\ge 0$
2. 规范性: 对于必然事件 $S$ , 有 $P(S) = 1$
3. 可列加性: 设 $A_1, A_2, \ldots$ 是两两互不相容的事件, 即对于 $A_iA_j = \emptyset, i \ne j, i, j = 1, 2, \ldots$ 有  
$$
P(A_1 \cup A_2 \ldots = P(A_1) + P(A_2) + \ldots
$$

性质:
* $P(\emptyset) = 0$
* 有限可加性: 若 $A_1, A_2, \ldots, A_n$ 是两两互不相容的事件, 则有  
$$
P(A_1 \cup A_2 \cup \ldots \cup A_n) = P(A_1) + P(A_2) + \ldots + P(A_n)
$$
* 设 $A, B$ 是两个事件, 若 $A \subset B$, 则有  
$$
P(B - A) = P(B) - P(A)
$$  
$$
P(B) \ge P(A)
$$
* 对于任意事件 $A$ ,  
$$
P(A) \le 1
$$
* 逆事件的概率: 对于任一事件 $A$ , 有  
$$
P(\overline{A}) = 1 - P(A)
$$
* 加法公式: 对于任意两事件 $A, B$有  
$$
P(A \cup B) = P(A) + P(B) - P(AB)
$$

## 等可能概型(古典概型)
等可能概型也称古典概型, 具有两个特点:
* 试验的样本空间只包含有限个元素
* 试验中的每个基本事件发生的可能性相同

古典概型中事件概率的计算公式: 设试验的样本空间 $S = \{e_1, e_2, \ldots, e_n\}$. 由于在试验中每个基本事件发生的可能性相同, 既有:  
$$
P(\{e_1\}) = P(\{e_2\}) = \ldots = P(\{e_n\})
$$
又由于基本事件是两两不相容的, 于是  
$$
\begin{align*}
1 &= P(S) \\
&= P(\{e_1\} \cup \{e_2\} \cup \ldots \cup \{e_n\}) \\
&= P(\{e_1\}) + P(\{e_2\}) + \ldots + P(\{e_n\}) \\
&= nP(\{e_i\}) \\
P(\{e_i\}) &= \frac{1}{n}, i = 1,2,\ldots,n
\end{align*}
$$
若事件 $A$ 包含 $k$ 个基本事件, 即 $A = \{e_{i_2}\} \cup \{e_{i_2}\} \cup \{e_{i_k}\}$, 这里 $i_1, i_2, \ldots, i_k$ 是 $1,2,\ldots,n$ 中某个 $k$ 个不同的数, 则有:  
$$
P(A) = \sum_{j=1}^{k}P(\{e_{i_j}\}) = \frac{k}{n} = \frac{A包含的基本事件数}{S中基本事件的总数}
$$
这就是等可能概型中事件A的概率计算公式.

## 条件概率
### 条件概率
在事件 $A$ 发生的条件下事件 $B$ 发生的概率(记为 $P(B|A)$ ).

定义: 设 $A,B$ 是两个事件, 且 $P(A) \gt 0$ , 称  
$$
P(B|A) = \frac{P(AB)}{P(A)}
$$
为在事件 $A$ 发生的条件下事件 $B$ 发生的**条件概率**.

条件概率 $P(\cdot|A)$ 符合概率定义中的三个条件:
1. 非负性: 对于每一个事件 $B$ , 有 $P(B|A) \ge 0$
2. 规范性: 对于必然事件 $S$ , 有 $P(S|A) = 1$
3. 可列可加性: 设 $B_1,B_2\dots$ 是两两互不相容的事件, 则有
$$
P(\bigcup\limits_{i=1}^{\infty}B_i|A) = \sum_{i=1}^{\infty}P(B_i|A)
$$
既然条件概率符合上述三个条件, 故对于任意事件 $B_1,B_2$ 有  
$$
P(B_1 \cup B_2 | A) = P(B_1|A) + P(B_2|A) - P(B_1B_2|A)
$$

### 乘法定理
定理: 设 $P(A) \gt 0$, 则有
$$
P(AB) = P(B|A)P(A)
$$
推广到多个时间的积事件情况: 设 $A,B,C$ 为事件, 且 $(P(AB) \gt 0)$ , 则有
$$
P(ABC)=P(C|AB)P(B|A)P(A)
$$
在这里, 注意到由假设 $P(AB) \gt 0$ 可推到得 $P(A) \ge P(AB) > 0$

一般, 设 $A_1,A_2,\ldots,A_n$ 为 $n$ 个事件, $n \ge 2$, 且 $P(A_1A_2\ldots A_{n-1}) \gt 0$, 则有:
$$
P(A_1A_2\ldots A_n) = P(A_n|A_1A_2\ldots A_{n-1})P(A_{n-1}|A_1A_2\ldots A_{n-2})\ldots P(A_2|A_1)P(A_1)
$$

### 全概率公式和贝叶斯公式
定义: 设 $S$ 为实验 $E$ 的样本空间, $B_1,B_2,\ldots,B_n$ 为 $E$ 的一组事件, 若:
* $B_iB_j = \emptyset, i \ne j, j = 1,2,\ldots,n$
* $B_1 \cup B_2 \cup \ldots \cup B_n = S$

则称 $B_1,B_2,\ldots,B_n$ 为样本空间的一个划分.

若 $B_1,B_2,\ldots,B_n$ 为样本空间的一个划分, 那么对于每次实验, 事件 $B_1,B_2,\ldots,B_n$ 中必有一个且仅有一个发生.

全概率公式: 设实验 $E$ 的样本空间为 $S$ ,  $A$ 为 $E$ 的事件, $B_1,B_2,\ldots,B_n$为 $S$ 的一个划分, 且 $P(B_i) \gt 0(i=1,2,\ldots,n)$ 则:
$$
P(A) = P(A|B_1)P(B_1) + P(A|B_2)P(B_2) + \ldots + P(A|B_n)P(B_n)
$$

贝叶斯公式: 设实验 $E$ 的样本空间为 $S$ ,  $A$ 为 $E$ 的事件, $B_1,B_2,\ldots,B_n$为 $S$ 的一个划分, 且 $P(A) \gt 0, P(B_i) \gt 0(i=1,2,\ldots,n)$, 则:
$$
P(B_i|A) = \frac{P(A|B_i)P(B_i)}{\sum_{j=1}^{n}P(A|B_j)P(B_j)}, i = 1,2,\ldots,n
$$

## 独立性
设 $A,B$ 是实验 $E$ 的两个事件, 若 $P(A) > 0$,可以定义 $P(B|A)$, 一般,  $A$ 的发生对 $B$ 发生的概率是**有影响**的, 这是 $P(B|A) \ne P(B)$,只有在这种影响不存在时才会有 $P(B|A) = P(B)$, 这时有:
$$
P(AB) = P(B|A)P(A)=P(A)P(B)
$$

$A,B$ 独立: 设 $A,B$ 是两个事件, 如果满足等式:
$$
P(AB)=P(A)P(B)
$$
则称事件 $A,B$ 相互独立.

定理:
* 设 $A,B$ 是两个事件, 且 $P(A) > 0$, 若 $A,B$ 相互独立, 则 $P(B|A)=P(B)$, 反之毅然.
* 若事件 $A$ 和 $B$ 相互独立, 则下列对事件也相互独立:
  * $A\ 与\ \overline{B}$
  * $\overline{A}\ 与\ B$
  * $\overline{A}\ 与\ \overline{B}$

$A,B,C$相互独立: 设 $A,B,C$ 是三个事件, 如果满足等式:
$$
\left.\begin{align*}
P(AB) &= P(A)P(B) \\
P(BC) &= P(B)P(C) \\
P(AC) &= P(A)P(C) \\
P(ABC) &= P(A)P(B)P(C)
\end{align*}\right\}
$$
则称事件 $A,B,C$ 相互独立.

# 随机变量及其分布
## 随机变量
随机变量: 设随机实验的样本空间为 $S=\{e\}$. $X=X(e)$ 是定义在样本空间 $S$ 上的实值单值函数, 称 $X=X(e)$ 为随机变量.

## 离散随机变量及其分布律
有些随机变量, 它全部可能取到的值是有限个或可列无限多个, 这种随机变量称之为离散型随机变量.

设离散型随机变量 $X$ 所有可能的取值为 $x_k(k=1,2,\ldots)$, $X$ 取各个可能值的概率, 即事件 $\{X=x_k\}$ 的概率为:
$$
P\{X=x_k\} = p_k, k=1,2,\ldots
$$
由概率的定义, $p_k$满足如下两个条件:
1. $p_k \ge 0, k=1,2,\ldots$
2. $\displaystyle\sum_{k=1}^{\infty}=1$
   2 是由于 $\displaystyle\{X=x_1\} \bigcup\limits_{k=1}^{\infty} \{X=x_k\}\ldots$是必然事件, 且 $\{X=x_j\} \cap \{X=x_k\} = \emptyset, k \ne j$, 故 $\displaystyle 1 = P[\bigcup\limits_{k=1}^{\infty}\{X=x_k\}] = \sum_{k=1}^{\infty}P\{X=x_k\}$. 即 $\displaystyle\sum_{k=1}^{\infty}P_k=1$

分布律也可以用表格表示:
| $X$   | $x_1$ | $x_2$ | $\ldots$ | $x_n$ | $\ldots$ |
| ----- | ----- | ----- | -------- | ----- | -------- |
| $p_k$ | $p_1$ | $p_2$ | $\ldots$ | $p_n$ | $\ldots$ |

### $(0-1)$分布
设随机变量 $X$ 只可能取0与1两个值, 它的分布规律是:
$$
P\{X=k\} = p^k(1-p)^{1-k},k=0,1
$$
则称 $X$ 服从 $p$ 为参数的 $(0-1)$ 分布或两点分布. $(0-1)$ 分布的分布律也可以写成:
| $X$   | 0     | 1   |
| ----- | ----- | --- |
| $p_k$ | $1-p$ | $p$ |

对于一个随机试验, 如果它的样本空间只包含两个元素, 即 $S=\{e_1,e_2\}$, 我们总能在 $S$ 上定义一个服从 $(0-1)$ 分布的随机变量:
$$
X=X(e)=\begin{cases}
0, & 当 e=e_1 \\
1, & 当 e=e_2
\end{cases}
$$

### 伯努利试验/二项分布
设试验 $E$ 只有两个可能结果: $A 及 \overline{A}$ , 则城 $E$ 为**伯努利**(*Bernoulli*)**试验**. 设 $P(A)=p(0<p<1)$ , 此时 $P(\overline{A})=1-p$. 将E独立重复地执行 $n$ 次, 则称一串重复的独立试验为 $n$ **重伯努利试验**. 即:
$$
P(C_1C_2\ldots C_n) = P(C_1)P(C_2)\ldots P(C_n)
$$
概率:
$$
\underbrace{p \cdot p \cdot \ldots \cdot p}_{k个} \cdot \underbrace{(1-p)\cdot(1-p)\cdot\ldots\cdot(1-p)}_{n-k个}=p^k(1-p)^{n-k}
$$
这种制定的方式共有
$$
\begin{pmatrix} n \\ k \end{pmatrix}
$$
种, 它们是两两互不相容的, 故在 $n$ 此实验中 $A$ 发生 $k$ 此的概率为 
$$
\begin{pmatrix} n \\ k \end{pmatrix}p^k(1-p)^{n-k}
$$
记 $q = 1 - p$ , 既有:
$$
P\{x=k\}=\begin{pmatrix} n \\ k \end{pmatrix}p^kq^{n-k},\  k=0,1,2,\cdots,n.
$$
显然
$$
P\{X=k\} \ge 0, k=0,1,2,\cdots,n;
$$
$$
\sum_{k=0}^{n}P\{X=k\}=\sum_{k=0}^{n}\begin{pmatrix} n \\ k \end{pmatrix}p^kq^{n-k}=(p+q)^n=1
$$
注意到 
$$
\begin{pmatrix} n \\ k \end{pmatrix} p^kq^{n-k}
$$
刚好是二项式 $(p+q)^n$ 的展开式中出现 $p^k$ 的那一项, 我们称随机变量 $X$ 服从参数为 $n,p$ 的二项分布, 并极为 $X \sim \mathcal{b}(n,p)$

### 泊松分布
设随机变量 $X$ 所有可能的取值为 $0,1,2,\cdots$ , 而取各个值的概率为
$$
P\{X=k\}=\frac{\lambda^k\mathrm{e}^{-\lambda}}{k!}, k=0,1,2,\cdots
$$
其中 $\lambda > 0$ 是常数, 则称 $X$ 服从参数为 $\lambda$ 的**泊松分布**, 记为 $X \sim \pi(\lambda)$

泊松定理: 设 $\lambda >0$ 是一个常数, $n$ 是任意正整数, 设 $np_n=\lambda$ , 则对于任一固定的非负整数 $k$ 有
$$
\lim_{n \to \infty}\begin{pmatrix} n \\ k \end{pmatrix}p_n^k(1-p)^{n-k} \approx \frac{\lambda^k\mathrm{e}^{-\lambda}}{k!}
$$
证, 由 $p_n=\frac{\lambda}{n}$ 有
$$
\begin{align*}
\begin{pmatrix} n \\ k \end{pmatrix}p_n^k(1-p)^{n-k} &= \frac{n(n-1)\cdots(n-k+1)}{k!}(\frac{\lambda}{n})^k(1-\frac{\lambda}{n})^{n-k} \\
&= \frac{\lambda^k}{k!}[1\cdot(1-\frac{1}{n})\cdots(1-\frac{k-1}{n})](1-\frac{\lambda}{n})^n(1-\frac{\lambda}{n})^{-k}
\end{align*}
$$
对于任意固定的 $k$, 当 $n \to \infty$ 时
$$
1\cdot(1-\frac{1}{n})\cdots(1-\frac{k-1}{n}) \to 1,\ (1-\frac{\lambda}{n})^n \to \mathrm{e}^{-\lambda},\ (1-\frac{\lambda}{n})^{-k} \to 1.
$$
故有
$$
\lim_{n \to \infty}\begin{pmatrix} n \\ k \end{pmatrix}p_n^k(1-p)^{n-k} \approx \frac{\lambda^k\mathrm{e}^{-\lambda}}{k!}
$$

## 随机变量的分布函数
定义 $X$ 是一个随机变量, $x$ 是任意实数, 函数
$$
E(x)=P\{X \le x\}, -\infty < x < \infty
$$
成为 $X$ 的分布函数. 

对于任意实数 $x_1,x_2(x_1<x_2)$ , 有
$$
\begin{align*}
P\{x_1 < X \le x_2\} &= P\{X \le x_2\} - P\{X \le x_1\} \\
&= F(x_2) - F(x_1)
\end{align*}
$$
因此, 若已知 $X$ 的分布函数, 我们就知道 $X$ 落在任一区间 $(x_1,x_2]$ 上的概率, 从这个意义上说, 分布函数完整的描述了随机变量的统计规律性.

分布函数 $F(x)$ 具有以下基本性质:
* $F(x)$ 是一个不减函数. 
  事实上, 对于任意实数 $x_1,x_2(x_1<x_2)$, 有
$$
F(x_2) - F(x_1) = P\{x_1< X \le x_2\} \ge 0
$$
* $0 \le F(x) \le 1$, 且
$$
\begin{align*}
F(-\infty) &= \lim_{x \to -\infty}F(x) = 0, \\
F(\infty) &= \lim_{x \to \infty}F(x) = 1.
\end{align*}
$$
* $F(x+0)=F(x)$, 即 $F(x)$ 是右连续的

## 连续随机变量及其概率密度
如果对于随机变量 $X$ 的分布函数 $F(x)$ , 存在非负函数 $f(x)$, 使对于任意实数 $x$ 有
$$
F(x) = \int_{-\infty}^{x}f(t)\mathrm{d}x
$$
则称 $X$ 为**连续随机变量**, 其中函数 $f(x)$ 称为 $X$ 的**概率密度函数**, 简称**概率密度**.

概率密度具有一下性质:
* $f(x) > 0$
* $\displaystyle\int_{-\infty}^{\infty}f(x)\mathrm{d}x=1$
* 对于任意实数 $x_1,x_2(x_1 \le x_2)$,
$$
P\{x_1 < X \le x_2\} = F(x_2) - F(x_1) = \int_{x_1}^{x_2}f(x)\mathrm{d}x
$$

### 均匀分布
若连续型随机变量 $X$ 具有概率密度为:
$$
f(x)=\begin{cases}
\displaystyle\frac{1}{b-a} && a < x < b \\
0 && 其他
\end{cases}
$$
则称 $X$ 在区间 $(a,b)$ 上服从**均匀分布**. 记作 $X \sim \mathcal{U}(a,b)$

### 指数分布
若连续型随机变量 $X$ 具有概率密度为:
$$
f(x)=\begin{cases}
\displaystyle\frac{1}{\theta}\mathrm{e}^{-x/\theta} && x>0\\
0 && 其他
\end{cases}
$$
其中 $\theta > 0$ 为常熟, 则称 $X$ 服从参数为 $\theta$ 的 **指数分布**.

### 正态分布
若连续型随机变量 $X$ 具有概率密度为:
$$
f(x)=\frac{1}{\sqrt{2\pi\delta}}\mathrm{e}^{-\frac{(x-\mu)^2}{2\delta^2}},-\infty < x < \infty
$$
其中 $\mu, \delta(\delta > 0)$ 为常数.则称 $X$ 服从参数为 $\mu,\delta$ 的**正态分布**或**高斯**(Gauss)分布, 记为 $X \sim \mathcal{N}(\mu,\delta^2)$

## 随机变量的函数的分布
**定理** 设随机变量 $X$ 具有概率密度 $f_X(x),-\infty<x<\infty$ , 有设函数 $g(x)$ 处处可导且恒有 $g'(x)>0$(或恒有 $g'(x)<0$ ), 则 $Y=g(X)$ 是连续型随机变量, 其概率密度为:
$$
f_Y(y)=\begin{cases}
f_X[h(y)]|h'(y)| && \alpha < y < \beta \\
0 && 其他
\end{cases}
$$
其中 $\alpha=\min\{g(-\infty),g(\infty)\}, \beta=\max\{g(-\infty),g(\infty)\}$, $h(y)$ 是 $g(x)$ 的反函数.

# 多维随机变量及其分布