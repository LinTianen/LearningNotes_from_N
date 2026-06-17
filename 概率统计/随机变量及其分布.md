## 随机变量
### 一、随机变量的定义
定义在样本空间 \(S\) 上的**实值单值函数** \(X=X(e)\)，取值随试验结果随机确定，且取值具有概率，记为 r.v.。

### 二、随机变量的特点
1. 试验前只知取值范围，不能确定具体取值
2. 取值具有对应概率
3. 与普通函数不同，定义域是样本空间而非实数区间

### 三、引入随机变量的意义
1. 把试验结果**数值化**，非数值结果也可量化（如抛硬币：正面1，反面0）
2. 用 \(X\) 的关系式表示事件，便于数学分析
3. 将事件概率研究扩展为**随机变量取值规律**的研究

### 四、随机变量的分类
1. **离散型**：取值为有限个或可列无限个值（如呼叫次数、次品数）
2. **连续型**：取值为某区间内全体实数（如寿命、测量误差）

## 离散型随机变量及其分布律
### 一、定义与分布律
离散型随机变量：所有可能取值为**有限个或可列无限个**。
分布律：\(P\{X=x_k\}=p_k\ (k=1,2,\dots)\)
满足：\(p_k\ge0\)，\(\displaystyle \sum_{k=1}^{\infty}p_k=1\)。
表示：公式法、列表法。

### 二、常见离散分布⭐
1. (0-1)分布：只取0、1，\(P(X=k)=p^k(1-p)^{1-k}\)。
2. 二项分布：\(X\sim b(n,p)\)，\(n\)重伯努利试验成功次数，\(P(X=k)=\mathrm C_n^kp^k(1-p)^{n-k}\)。
3. 泊松分布：\(X\sim\pi(\lambda)\)，\(\displaystyle P(X=k)=\frac{\lambda^k}{k!}e^{-\lambda}\)。
4. 超几何分布：不放回抽样，\(\displaystyle P(X=k)=\frac{\mathrm C_M^k\mathrm C_{N-M}^{n-k}}{\mathrm C_N^n}\)。
5. 几何分布：首次成功试验次数，\(P(X=k)=(1-p)^{k-1}p\)。

### 三、重要结论
- 二项分布可由\(n\)个(0-1)分布叠加得到。
- **\(n\)大\(p\)小时，二项分布可用泊松分布近似**，\(\lambda=np\)。
- 离散型随机变量的概率规律由**分布律唯一确定**。
  
## 随机变量的分布函数
### 一、定义
设 \(X\) 是随机变量，对任意实数 \(x\)，称
\[
F(x)=P\{X\leq x\}
\]
为 \(X\) 的分布函数，定义域为 \((-\infty,+\infty)\)。

### 二、核心意义
- 表示 \(X\) 落在 \((-\infty,x]\) 内的概率
- 统一描述离散型与连续型随机变量
- 可用高等数学方法研究随机变量

### 三、基本性质
1. 单调不减：\(x_1<x_2 \Rightarrow F(x_1)\leq F(x_2)\)
2. 有界性：\(F(-\infty)=0,\ F(+\infty)=1\)
3. 右连续：\(\lim\limits_{x\to x_0^+}F(x)=F(x_0)\)

### 四、离散型的分布函数
由分布律累加得到：
\[
F(x)=\sum_{x_k\leq x}p_k
\]
图形为**阶梯曲线**，在取值点处跳跃，跳跃值为对应概率。

## 连续型随机变量及其概率密度
### 一、定义
若存在非负可积函数 \(f(x)\)，对任意实数 \(x\) 有
\[
F(x)=\int_{-\infty}^x f(t)dt
\]
则称 \(X\) 为**连续型随机变量**，\(f(x)\) 为**概率密度函数**。

### 二、概率密度的性质
1. \(f(x)\ge0\)
2. \(\displaystyle\int_{-\infty}^{+\infty}f(x)dx=1\)
3. \(\displaystyle P\{x_1<X\le x_2\}=\int_{x_1}^{x_2}f(x)dx\)
4. 若 \(f(x)\) 在 \(x\) 连续，则 \(F'(x)=f(x)\)

### 三、重要结论
- 连续型随机变量取**单点概率为 0**，即 \(P\{X=a\}=0\)
- \(P\{a<X\le b\}=P\{a\le X\le b\}=P\{a<X<b\}\)

### 四、三种常用连续分布⭐
1. **均匀分布 \(U(a,b)\)**
\[
f(x)=
\begin{cases}
\dfrac{1}{b-a},&a<x<b\\
0,&\text{其他}
\end{cases}
\]
分布函数：
\[
F(x)=
\begin{cases}
0,&x<a\\
\dfrac{x-a}{b-a},&a\le x<b\\
1,&x\ge b
\end{cases}
\]
特点：等长度子区间概率相等，对应一维几何概型。

2. **指数分布 \(E(\theta)\)**
\[
f(x)=
\begin{cases}
\dfrac{1}{\theta}e^{-x/\theta},&x>0\\
0,&x\le 0
\end{cases}
\]
分布函数：
\[
F(x)=
\begin{cases}
1-e^{-x/\theta},&x>0\\
0,&x\le 0
\end{cases}
\]
核心性质：**无记忆性**
\[
P\{X>s+t\mid X>s\}=P\{X>t\}
\]
应用：寿命、等待时间。

3. **正态分布 \(N(\mu,\sigma^2)\)**
概率密度：
\[
f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{\displaystyle-\frac{(x-\mu)^2}{2\sigma^2}}
\]
- \(\mu\)：位置参数，决定中心
- \(\sigma\)：尺度参数，决定陡峭程度

标准正态分布 \(N(0,1)\)：
\[
\varphi(x)=\frac{1}{\sqrt{2\pi}}e^{\displaystyle-\frac{x^2}{2}},\quad \Phi(x)=\int_{-\infty}^x\varphi(t)dt
\]
标准化变换：
\[
X\sim N(\mu,\sigma^2)\implies Z=\frac{X-\mu}{\sigma}\sim N(0,1)
\]
概率计算：
\[
P\{a<X<b\} =\Phi\left(\frac{b-\mu}{\sigma}\right)-\Phi\left(\frac{a-\mu}{\sigma}\right)
\]
\(3\sigma\) 准则：
\[
P\{|X-\mu|\le 3\sigma\}\approx0.9974
\]


## 随机变量的函数的分布
### 一、离散型随机变量函数的分布
已知 \(X\) 的分布律，求 \(Y=g(X)\) 的分布律：
1. 直接计算 \(Y\) 的所有可能取值 \(g(x_k)\)
2. 相同取值合并，对应概率相加
3. 写出 \(Y\) 的分布律

### 二、连续型随机变量函数的分布
通用步骤：
1. 求 \(Y\) 的分布函数：
\[
F_Y(y)=P\{Y\le y\}=P\{g(X)\le y\}
\]
2. 将不等式转化为关于 \(X\) 的区间
3. 对 \(F_Y(y)\) 求导得概率密度：
\[
f_Y(y)=F_Y'(y)
\]

### 三、单调函数公式法（定理）⭐
若 \(y=g(x)\) 处处可导且恒有 \(g'(x)>0\) 或 \(g'(x)<0\)，则
\[
f_Y(y)=
\begin{cases}
f_X[h(y)]\left|h'(y)\right|, & \alpha<y<\beta\\
0, & else
\end{cases}
\]
其中 \(x=h(y)\) 是 \(y=g(x)\) 的反函数。

### 四、常用结论
1. \(Y=X^2\) 的密度：
\[
f_Y(y)=
\begin{cases}
\displaystyle\frac{1}{2\sqrt{y}}\left[f_X(\sqrt{y})+f_X(-\sqrt{y})\right], & y>0\\
0, & y\le0
\end{cases}
\]
2. 正态分布线性不变性：
\[
X\sim N(\mu,\sigma^2)\implies Y=aX+b\sim N(a\mu+b,a^2\sigma^2)
\]
3. 分布函数变换：若 \(F_X(x)\) 严格单调连续，则 \(Y=F_X(X)\sim U(0,1)\)