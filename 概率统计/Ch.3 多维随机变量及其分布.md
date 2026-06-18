## 二维随机变量
### 一、联合分布函数
设 \((X,Y)\) 为二维随机变量，称
\[
F(x,y)=P\{X\le x,Y\le y\}
\]
为**联合分布函数**，表示随机点落在 \((x,y)\) 左下方无穷矩形内的概率。

#### 性质
1. 对 \(x,y\) 均**单调不减**
2. \(0\le F(x,y)\le 1\)，且
\[
F(-\infty,y)=0,\quad F(x,-\infty)=0,\quad F(+\infty,+\infty)=1
\]
3. **右连续**：\(F(x,y)=F(x+0,y)=F(x,y+0)\)

### 二、二维离散型随机变量
若 \((X,Y)\) 只取有限对或可列无限多对值，称为离散型。
联合分布律：
\[
P\{X=x_i,Y=y_j\}=p_{ij}
\]
满足：
\[
p_{ij}\ge0,\quad \sum_i\sum_j p_{ij}=1
\]
分布函数：
\[
F(x,y)=\sum_{x_i\le x}\sum_{y_j\le y}p_{ij}
\]

### 三、二维连续型随机变量
若存在非负可积函数 \(f(x,y)\)，使得
\[
F(x,y)=\int_{-\infty}^y\int_{-\infty}^x f(u,v)dudv
\]
则称 \((X,Y)\) 为连续型，\(f(x,y)\) 为**联合概率密度**。

#### 性质
1. \(f(x,y)\ge0\)
2. \(\displaystyle\iint_{\mathbb R^2}f(x,y)dxdy=1\)
3. 平面区域 \(G\) 上的概率：
\[
P\{(X,Y)\in G\}=\iint_G f(x,y)dxdy
\]
4. 连续点处：\(\displaystyle f(x,y)=\frac{\partial^2F(x,y)}{\partial x\partial y}\)

### 四、常用结论
- 离散型：由表格给出联合分布，按取值求和
- 连续型：概率用**二重积分**计算，注意积分区域划分

## 边缘分布
### 一、边缘分布函数
由联合分布函数 \(F(x,y)\) 可得边缘分布：
\[
F_X(x)=F(x,+\infty),\quad F_Y(y)=F(+\infty,y)
\]

### 二、离散型的边缘分布律
联合分布律：\(P\{X=x_i,Y=y_j\}=p_{ij}\)
- 关于 \(X\)：\(\displaystyle p_{i\cdot}=\sum_j p_{ij}\)
- 关于 \(Y\)：\(\displaystyle p_{\cdot j}=\sum_i p_{ij}\)

### 三、连续型的边缘概率密度
联合密度 \(f(x,y)\)，则：
\[
f_X(x)=\int_{-\infty}^{+\infty}f(x,y)dy,\quad
f_Y(y)=\int_{-\infty}^{+\infty}f(x,y)dx
\]

### 四、重要结论
1. 联合分布 **唯一确定** 边缘分布
2. 边缘分布 **一般不能** 确定联合分布
3. 二维均匀分布的边缘分布 **不一定** 是均匀分布
4. 二维正态分布 \(N(\mu_1,\mu_2,\sigma_1^2,\sigma_2^2,\rho)\) 的边缘分布为：
\[
X\sim N(\mu_1,\sigma_1^2),\quad Y\sim N(\mu_2,\sigma_2^2)
\]
与 \(\rho\) 无关。

## 条件分布
### 一、离散型条件分布律
设联合分布律 \(P\{X=x_i,Y=y_j\}=p_{ij}\)，边缘分布 \(p_{i\cdot},p_{\cdot j}\)。
1. 在 \(Y=y_j\) 条件下 \(X\) 的条件分布律：
\[
P\{X=x_i\mid Y=y_j\}=\frac{p_{ij}}{p_{\cdot j}}
\]
2. 在 \(X=x_i\) 条件下 \(Y\) 的条件分布律：
\[
P\{Y=y_j\mid X=x_i\}=\frac{p_{ij}}{p_{i\cdot}}
\]
条件分布满足非负性且和为 1。

### 二、连续型条件概率密度
设联合密度 \(f(x,y)\)，边缘密度 \(f_X(x),f_Y(y)\)。
1. 在 \(Y=y\) 条件下 \(X\) 的条件密度：
\[
f_{X\mid Y}(x\mid y)=\frac{f(x,y)}{f_Y(y)}
\]
2. 在 \(X=x\) 条件下 \(Y\) 的条件密度：
\[
f_{Y\mid X}(y\mid x)=\frac{f(x,y)}{f_X(x)}
\]
3. 条件分布函数：
\[
F_{X\mid Y}(x\mid y)=\int_{-\infty}^x f_{X\mid Y}(u\mid y)du
\]

### 三、常用关系
- 乘法公式：\(f(x,y)=f_X(x)\cdot f_{Y\mid X}(y\mid x)\)
- 联合分布唯一确定条件分布，条件分布可用于求边缘或联合分布。
## 相互独立的随机变量
### 一、独立的定义
对任意实数 \(x,y\)，若
\[
F(x,y)=F_X(x)F_Y(y)
\]
则称 \(X\) 与 \(Y\) **相互独立**。

### 二、离散型独立性判定
对所有可能取值 \((x_i,y_j)\)，满足
\[
P\{X=x_i,Y=y_j\}=P\{X=x_i\}P\{Y=y_j\}
\]
等价于：
\[
p_{ij}=p_{i\cdot}p_{\cdot j}
\]

### 三、连续型独立性判定
对几乎所有 \((x,y)\)，满足
\[
f(x,y)=f_X(x)f_Y(y)
\]
等价于条件密度等于边缘密度：
\[
f_{X|Y}(x|y)=f_X(x),\quad f_{Y|X}(y|x)=f_Y(y)
\]

### 四、重要结论
1. 独立时，**边缘分布可唯一确定联合分布**
2. 矩形域上二维均匀分布，\(X,Y\) 必独立
3. 独立随机变量的函数仍独立：若 \(X,Y\) 独立，则 \(g(X),h(Y)\) 独立
4. 独立分布可加性
- 二项分布：\(X\sim B(n_1,p),Y\sim B(n_2,p)\) 独立 \(\Rightarrow X+Y\sim B(n_1+n_2,p)\)
- 泊松分布：\(X\sim P(\lambda_1),Y\sim P(\lambda_2)\) 独立 \(\Rightarrow X+Y\sim P(\lambda_1+\lambda_2)\)

### 五、n维随机变量独立
联合分布函数等于各边缘分布函数的乘积：
\[
F(x_1,\dots,x_n)=F_{X_1}(x_1)\cdots F_{X_n}(x_n)
\]
## 两个随机变量的函数的分布
### 一、离散型函数分布
已知联合分布律 \(P\{X=x_i,Y=y_j\}=p_{ij}\)，求 \(Z=g(X,Y)\)：
1. 列出所有 \((X,Y)\) 对应 \(Z\) 的取值
2. 相同取值合并，概率相加
3. 写出 \(Z\) 的分布律

**可加性结论**
- 二项分布：\(X\sim B(n_1,p),Y\sim B(n_2,p)\) 独立 \(\Rightarrow X+Y\sim B(n_1+n_2,p)\)
- 泊松分布：\(X\sim P(\lambda_1),Y\sim P(\lambda_2)\) 独立 \(\Rightarrow X+Y\sim P(\lambda_1+\lambda_2)\)

### 二、连续型和分布 \(Z=X+Y\)
一般公式：
\[
f_Z(z)=\int_{-\infty}^{+\infty}f(x,z-x)dx
\]
独立时（卷积公式）：
\[
f_Z(z)=\int_{-\infty}^{+\infty}f_X(x)f_Y(z-x)dx
\]

**正态可加性**
若 \(X\sim N(\mu_1,\sigma_1^2),Y\sim N(\mu_2,\sigma_2^2)\) 独立，则
\[
X+Y\sim N(\mu_1+\mu_2,\sigma_1^2+\sigma_2^2)
\]
线性组合仍正态。

### 三、最值分布（\(X,Y\) 独立）
1. \(M=\max(X,Y)\)
\[
F_M(z)=F_X(z)F_Y(z)
\]
2. \(N=\min(X,Y)\)
\[
F_N(z)=1-[1-F_X(z)][1-F_Y(z)]
\]

推广到 \(n\) 个独立同分布变量：
\[
F_{\max}(z)=[F(z)]^n,\quad F_{\min}(z)=1-[1-F(z)]^n
\]
