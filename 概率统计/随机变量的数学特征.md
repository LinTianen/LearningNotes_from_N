## 期望
### 一、离散型随机变量的数学期望
**定义**
设离散型随机变量\(X\)的分布律为\(P\{X=x_k\}=p_k\ (k=1,2,\dots)\)，若级数\(\displaystyle\sum_{k=1}^{\infty}x_kp_k\)**绝对收敛**，则：
\[E(X)=\sum_{k=1}^{\infty}x_kp_k\]
**关键说明**
- \(E(X)\)是**实数**，非变量；
- 绝对收敛保证和与项的次序无关；
- 等概率时，期望=算术平均值。

### 二、连续型随机变量的数学期望
**定义**
设连续型随机变量\(X\)的概率密度为\(f(x)\)，若积分\(\displaystyle\int_{-\infty}^{+\infty}xf(x)dx\)**绝对收敛**，则：
\[E(X)=\int_{-\infty}^{+\infty}xf(x)dx\]

### 三、随机变量函数的数学期望
#### 1. 一维情形
设\(Y=g(X)\)（\(g\)连续），无需求\(Y\)的分布：
- 离散型：\(E[g(X)]=\displaystyle\sum_{k=1}^{\infty}g(x_k)p_k\)
- 连续型：\(E[g(X)]=\displaystyle\int_{-\infty}^{+\infty}g(x)f(x)dx\)

#### 2. 二维情形
设\(Z=g(X,Y)\)：
- 离散型：\(E(Z)=\displaystyle\sum_i\sum_jg(x_i,y_j)p_{ij}\)
- 连续型：\(E(Z)=\displaystyle\iint_{-\infty}^{+\infty}g(x,y)f(x,y)dxdy\)

### 四、数学期望的性质
1. 常数的期望：\(E(C)=C\)
2. 数乘性质：\(E(kX)=kE(X)\)
3. 和的性质：\(E(X+Y)=E(X)+E(Y)\)（**不要求独立**）
    推广：\(\displaystyle E\left(\sum_{i=1}^nX_i\right)=\sum_{i=1}^nE(X_i)\)
4. 积的性质：\(X,Y\)独立\(\Rightarrow E(XY)=E(X)E(Y)\)
    推广：独立变量乘积的期望=期望的乘积

## 方差
### 一、定义
设随机变量 \(X\)，若 \(E\left\{[X-E(X)]^2\right\}\) 存在，则：
\[
D(X)=\operatorname{Var}(X)=E\left\{[X-E(X)]^2\right\}
\]
- **标准差**：\(\sigma(X)=\sqrt{D(X)}\)，与 \(X\) 同量纲。
- **含义**：衡量 \(X\) 与均值的平均平方偏差。

### 二、计算
1. 按定义计算
   - 离散型：
\(\displaystyle D(X)=\sum_{k=1}^{\infty}\left[x_k-E(X)\right]^2 p_k
\)
   - 连续型：
\(\displaystyle D(X)=\int_{-\infty}^{+\infty}\left[x-E(X)\right]^2 f(x)dx
\)

1. 简化公式
\[
{D(X)=E(X^2)-[E(X)]^2}
\]

### 三、常用分布的期望与方差（必背）⭐
| 分布 | 记号 | \(E(X)\) | \(D(X)\) |
| :--- | :--- | :--- | :--- |
| 0-1分布 | \(B(1,p)\) | \(p\) | \(p(1-p)\) |
| 二项分布 | \(B(n,p)\) | \(np\) | \(np(1-p)\) |
| 泊松分布 | \(P(\lambda)\) | \(\lambda\) | \(\lambda\) |
| 均匀分布 | \(U(a,b)\) | \(\frac{a+b}{2}\) | \(\frac{(b-a)^2}{12}\) |
| 指数分布 | \(E(\theta)\) | \(\theta\) | \(\theta^2\) |
| 正态分布 | \(N(\mu,\sigma^2)\) | \(\mu\) | \(\sigma^2\) |

### 四、方差的性质
1. 常数：\(D(C)=0\)
2. 数乘与平移：
\[
D(CX)=C^2D(X),\quad D(X+C)=D(X)
\]
3. 和的方差（通用）：
\[
D(X+Y)=D(X)+D(Y)+2E\left\{[X-E(X)][Y-E(Y)]\right\}
\]
4. **独立**时：
\[
D(X+Y)=D(X)+D(Y)
\]
5. 推广：独立随机变量线性组合
\[
D\left(\sum C_iX_i\right)=\sum C_i^2D(X_i)
\]
6. 充要条件：\(D(X)=0\iff P\{X=E(X)\}=1\)

### 五、切比雪夫不等式
设 \(E(X)=\mu\)，\(D(X)=\sigma^2\)，对任意 \(\varepsilon>0\)：
\[
P\left\{|X-\mu|\ge\varepsilon\right\}\le\frac{\sigma^2}{\varepsilon^2}
\]
等价形式：
\[
P\left\{|X-\mu|<\varepsilon\right\}\ge 1-\frac{\sigma^2}{\varepsilon^2}
\]

**常用结论**
- \(P\left\{|X-\mu|\ge k\sigma\right\}\le\displaystyle\frac{1}{k^2}\)
- \(k=2\)：\(\le 1/4\)；\(k=3\)：\(\le 1/9\)
- 适用：**任意分布**，仅需期望、方差存在。

### 六、典型应用
1. **分解法求方差**：把复杂变量拆为独立0-1变量之和，用方差可加性计算（如二项分布）。
2. **正态线性组合**：独立正态变量的线性组合仍正态，直接算期望与方差。
3. **概率粗略估计**：分布未知时，用切比雪夫不等式给出下界/上界。

## 协方差
### 1. 定义
设二维随机变量 \((X,Y)\)，若 \(E\left\{[X-E(X)][Y-E(Y)]\right\}\) 存在，则称其为 \(X\) 与 \(Y\) 的**协方差**，记为：
\[
\text{Cov}(X,Y)=E\left\{[X-E(X)][Y-E(Y)]\right\}
\]

### 2. 核心性质
1. 对称性：\(\text{Cov}(X,Y)=\text{Cov}(Y,X)\)
2. 数乘性：\(\text{Cov}(aX,bY)=ab\cdot\text{Cov}(X,Y)\)
3. 可加性：\(\text{Cov}(X_1+X_2,Y)=\text{Cov}(X_1,Y)+\text{Cov}(X_2,Y)\)

### 3. 常用计算公式
\[
\text{Cov}(X,Y)=E(XY)-E(X)\cdot E(Y)
\]

### 4. 与方差的关系⭐
\[
D(X+Y)=D(X)+D(Y)+2\text{Cov}(X,Y)
\]

### 5. 相关性判断
- \(\text{Cov}(X,Y)>0\)：**正相关**
- \(\text{Cov}(X,Y)<0\)：**负相关**
- \(\text{Cov}(X,Y)=0\)：**不相关（线性无关）**

## 相关系数
### 1. 定义
设 \(D(X)>0,D(Y)>0\)，称
\[
\rho_{XY}=\frac{\text{Cov}(X,Y)}{\sqrt{D(X)}\cdot\sqrt{D(Y)}}
\]
为 \(X\) 与 \(Y\) 的**相关系数**（无量纲）。

### 2. 核心性质
1. 有界性：\(|\rho_{XY}|\le 1\)
2. \(X,Y\) 相互独立 \(\Rightarrow \rho_{XY}=0\)（不相关）；但 \(\rho_{XY}=0\) **不一定**推出独立
3. \(|\rho_{XY}|=1\Leftrightarrow\) 存在常数 \(a,b(b\ne0)\)，使得 \(P\{Y=a+bX\}=1\)（完全线性相关）

### 3. 线性相关程度
- \(|\rho|\) 越接近 \(1\)：线性关系越强
- \(|\rho|\) 越接近 \(0\)：线性关系越弱
- \(\rho=0\)：无线性关系，但可存在非线性关系

## 三、重要结论
1. 独立 \(\Rightarrow\) 不相关；不相关 \(\nRightarrow\) 独立
2. 二维正态分布 \((X,Y)\sim N(\mu_1,\mu_2,\sigma_1^2,\sigma_2^2,\rho)\)：
   - \(\text{Cov}(X,Y)=\rho\sigma_1\sigma_2\)
   - \(\rho_{XY}=\rho\)
   - **独立 \(\Leftrightarrow\) 不相关**（等价）
  
## 矩与协方差矩阵
### 一、矩
1. 原点矩
设 \(X\) 为随机变量，若 \(E(X^k)\) 存在，称为 \(X\) 的 **\(k\) 阶原点矩**，\(k=1,2,\dots\)
   - 一阶原点矩：\(E(X)\)（数学期望）

2. 中心矩
若 \(E\left\{[X-E(X)]^k\right\}\) 存在，称为 \(X\) 的 **\(k\) 阶中心矩**，\(k=2,3,\dots\)
   - 二阶中心矩：\(D(X)\)（方差）

1. 混合矩
   - \(k+l\) 阶混合原点矩：\(E(X^k Y^l)\)
   - \(k+l\) 阶混合中心矩：\(E\left\{[X-E(X)]^k [Y-E(Y)]^l\right\}\)
   - 协方差 \(\text{Cov}(X,Y)\) 是 **二阶混合中心矩**

### 二、协方差矩阵
#### 1. 二维协方差矩阵
设二维随机变量 \((X_1,X_2)\)，记
\[
c_{ij}=\text{Cov}(X_i,X_j)=E\left\{[X_i-E(X_i)][X_j-E(X_j)]\right\}
\]
协方差矩阵：
\[
C=
\begin{pmatrix}
c_{11}&c_{12}\\
c_{21}&c_{22}
\end{pmatrix}
\]
- \(c_{11}=D(X_1)\)，\(c_{22}=D(X_2)\)，\(c_{12}=c_{21}=\text{Cov}(X_1,X_2)\)

#### 2. \(n\) 维协方差矩阵
对 \(n\) 维随机变量 \((X_1,X_2,\dots,X_n)\)
\[
c_{ij}=\text{Cov}(X_i,X_j),\quad i,j=1,2,\dots,n
\]
协方差矩阵：
\[
C=
\begin{pmatrix}
c_{11}&c_{12}&\dots&c_{1n}\\
c_{21}&c_{22}&\dots&c_{2n}\\
\vdots&\vdots&\ddots&\vdots\\
c_{n1}&c_{n2}&\dots&c_{nn}
\end{pmatrix}
\]
矩阵对称、半正定，用于表示多维随机变量分布。

### 三、\(n\) 元正态分布
#### 1. 概率密度
设 \(X=(x_1,x_2,\dots,x_n)^T\)，期望向量 \(\mu=(E(X_1),\dots,E(X_n))^T\)，协方差矩阵 \(C\)，则
\[
f(x_1,\dots,x_n)=\frac{1}{(2\pi)^{n/2}|C|^{1/2}}\exp\left\{-\frac{1}{2}(X-\mu)^T C^{-1}(X-\mu)\right\}
\]

#### 2. 重要性质
1. \(n\) 维正态分量均为一维正态变量；独立一维正态可构成 \(n\) 维正态。
2. 任意线性组合 \(l_1X_1+\dots+l_nX_n\) 服从一维正态。
3. 线性变换不变性：正态变量的线性变换仍为正态。
4. \(n\) 维正态中，**相互独立** \(\iff\) **两两不相关**。
