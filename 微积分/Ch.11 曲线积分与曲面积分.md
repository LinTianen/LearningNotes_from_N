# 曲线积分与曲面积分

# 第一节 对弧长的曲线积分

## 一、定义

设 $L$ 为平面光滑曲线弧，函数 $f(x,y)$ 在 $L$ 上有界，将 $L$ 任意分成 $n$ 个小弧段 $\Delta s_i$ ，在每个小弧段上任取一点 $(\xi_i,\eta_i)$ ，若极限 $\displaystyle \lim\limits_{\lambda \to 0}\sum\limits_{i=1}^n f(\xi_i,\eta_i)\Delta s_i$ 存在（ $\lambda$ 为最大弧段长度），则称该极限为 $f(x,y)$ 在曲线 $L$ 上对弧长的曲线积分，记作：$\displaystyle \int_L f(x,y)ds$ 

空间曲线弧 $\Gamma$ 的推广形式： $\displaystyle \int_\Gamma f(x,y,z)ds$ 

## 二、物理与几何意义

1. 物理意义：若 $f(x,y)\geq0$ ，表示线密度为 $f(x,y)$ 的曲线型构件的**质量**；

2. 几何意义：当 $f(x,y)=1$ 时， $\displaystyle \int_L ds$ 表示曲线 $L$ 的**弧长**。

## 三、基本性质

1. 无方向性：对弧长的曲线积分与曲线的走向无关，即 $\displaystyle \int_{L^-} f(x,y)ds=\int_L f(x,y)ds$ （ $L^-$ 为 $L$ 反向曲线）；

2. 线性性质： $\displaystyle \int_L [k_1f+k_2g]ds=k_1\int_L fds+k_2\int_L gds$ （ $k_1,k_2$ 为常数）；

3. 可加性：若 $L=L_1+L_2$ ，则 $\displaystyle \int_L fds=\int_{L_1} fds+\int_{L_2} fds$ 。

## 四、核心计算公式（参数化法）

1. 平面曲线参数方程：设 $L:\begin{cases}x=\varphi(t)\\y=\psi(t)\end{cases} (\alpha\leq t\leq\beta)$ ， $\varphi(t),\psi(t)$ 连续可导，则：

    $\displaystyle \int_L f(x,y)ds=\int_\alpha^\beta f[\varphi(t),\psi(t)]\sqrt{\varphi'^2(t)+\psi'^2(t)}dt$ 

2. 关键规则：**积分下限≤上限**（弧长元素 $ds>0$ ，恒保证积分结果为正）；

3. 特殊形式：
   - 直角坐标 $y=y(x)(a\leq x\leq b)$ ，则 $ds=\sqrt{1+y'^2}dx$ 
   - 极坐标 $r=r(\theta)(\alpha\leq\theta\leq\beta)$ ，则 $ds=\sqrt{r^2(\theta)+r'^2(\theta)}d\theta$ 

# 第二节 对坐标的曲线积分

## 一、定义

设 $L$ 为平面有向光滑曲线弧，向量函数 $\vec{F}(x,y)=P(x,y)\vec{i}+Q(x,y)\vec{j}$ ，定义对坐标的曲线积分：

 $\displaystyle \int_L Pdx+Qdy=\int_L Pdx+\int_L Qdy$ 

空间推广： $\displaystyle \int_\Gamma Pdx+Qdy+Rdz$ 

## 二、物理意义

表示变力 $\vec{F}(x,y)$ 沿有向曲线 $L$ 做功的大小，是力学中变力做功的数学表达。

## 三、基本性质（核心区别于第一类）

1. **有方向性**：反向曲线积分变号， $\displaystyle \int_{\boldsymbol{L^-}} Pdx+Qdy=-\int_L Pdx+Qdy$ （高频考点）；

2. 线性、可加性与第一类曲线积分一致，拆分曲线时需保留对应方向。

## 四、核心计算公式

设有向曲线 $L:\begin{cases}x=\varphi(t)\\y=\psi(t)\end{cases} (t:\alpha\to\beta)$ （ $\alpha$ 为起点参数， $\beta$ 为终点参数），则：

 $\displaystyle \int_L Pdx+Qdy=\int_\alpha^\beta \big\{P[\varphi(t),\psi(t)]\varphi'(t)+Q[\varphi(t),\psi(t)]\psi'(t)\big\}dt$ 

关键规则：**积分上下限严格对应曲线起点、终点参数**，下限可大于上限。

## 五、两类曲线积分的联系

 $\displaystyle \int_L Pdx+Qdy=\int_L (P\cos\alpha+Q\cos\beta)ds$ 

其中 $\cos\alpha,\cos\beta$ 为有向曲线 $L$ 上点的**切向量方向余弦**。

# 第三节 格林公式及其运用

## 一、格林公式核心内容

设闭区域 $D$ 由分段光滑的闭曲线 $L$ 围成，函数 $P(x,y),Q(x,y)$ 在 $D$ 上具有一阶连续偏导数，则有：

 $\displaystyle \oint_L Pdx+Qdy=\iint_D \big(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}\big)dxdy$ 

**方向要求**： $L$ 为区域 $D$ 的**正向边界曲线**（逆时针为正，顺时针为负）。

## 二、区域分类

1. 单连通区域：区域内任意闭曲线围成的区域均含于原区域（无“洞”）；

2. 复连通区域：区域含空心洞，格林公式需取外边界正向、内边界负向（外逆内顺）。

## 三、四大核心应用

### 1. 计算闭曲线积分

直接将第二类闭曲线积分转化为二重积分，简化复杂曲线计算；非闭曲线可**补线成闭曲线**，再减去补线的积分值（补线法高频解题）。

### 2. 求平面图形面积

令 $P=-\dfrac{y}{2},Q=\dfrac{x}{2}$ ，得面积公式： $\displaystyle S=\frac{1}{2}\oint_L xdy-ydx$ 。

### 3. 平面曲线积分与路径无关

在单连通区域内， $\displaystyle \int_L Pdx+Qdy$ 与路径无关 $\iff \dfrac{\partial Q}{\partial x}=\dfrac{\partial P}{\partial y}$ ，仅与起点、终点有关。

解题技巧：与路径无关时，可替换为平行坐标轴的折线路径计算积分，大幅简化运算。

### 4. 求二元函数原函数

若 $\dfrac{\partial Q}{\partial x}=\dfrac{\partial P}{\partial y}$ ，则存在 $u(x,y)$ 使得 $du=Pdx+Qdy$ ，原函数可通过折线积分求解：

 $\displaystyle u(x,y)=\int_{x_0}^x P(x,y_0)dx+\int_{y_0}^y Q(x,y)dy$ 

## 四、易错要点

1. 必须满足“一阶连续偏导数”条件，不满足则不能直接用格林公式；

2. 边界曲线方向必须为正向，反向需加负号；

3. 区域含奇点（偏导数不存在/不连续点）时，需挖去奇点后用复连通格林公式。

# 第四节 对面积的曲面积分

## 一、定义

设 $\Sigma$ 为光滑曲面，函数 $f(x,y,z)$ 在 $\Sigma$ 上有界，分割曲面、取点、求和、取极限，得对面积的曲面积分：

 $\displaystyle \iint_\Sigma f(x,y,z)dS$ 

## 二、意义与性质

1. 物理意义：面密度为 $f(x,y,z)$ 的曲面薄片的质量；

2. 几何意义： $f=1$ 时，积分结果为曲面 $\Sigma$ 的面积；

3. 性质：**无方向性**，与曲面侧无关，满足线性、可加性。

## 三、核心计算公式（投影法）

设曲面 $\Sigma:z=z(x,y)$ ，投影到 $xOy$ 平面得区域 $D_{xy}$ ， $z(x,y)$ 连续可导，则：

 $\displaystyle \iint_\Sigma f(x,y,z)dS=\iint_{D_{xy}} f[x,y,z(x,y)]\sqrt{1+z_x^2+z_y^2}dxdy$ 

同理可投影到 $yOz$ 、 $xOz$ 平面，适配不同曲面方程； $dS>0$ **面积元素，投影区域恒为正**。

# 第五节 对坐标的曲面积分

## 一、定义

设 $\Sigma$ 为有向光滑曲面，定义三类对坐标的曲面积分，合并形式为：

 $\displaystyle \iint_\Sigma P dydz+Q dzdx+R dxdy$ 

## 二、物理意义

表示流速为 $\vec{v}=(P,Q,R)$ 的稳定流体通过有向曲面 $\Sigma$ 的**通量**。

## 三、核心性质

**有方向性**：曲面取反向侧 $\Sigma^-$ 时，积分变号：

 $\displaystyle \iint_{\boldsymbol{\Sigma^-}} P dydz+Q dzdx+R dxdy=-\iint_\Sigma P dydz+Q dzdx+R dxdy$ 

## 四、投影计算规则（重中之重）

1.  $\displaystyle \iint_\Sigma Rdxdy$ ：投影到 $xOy$ 面，上侧为正、下侧为负，曲面垂直 $xOy$ 面时积分=0；

2.  $\displaystyle \iint_\Sigma Qdzdx$ ：投影到 $xOz$ 面，右侧为正、左侧为负，曲面垂直 $xOz$ 面时积分=0；

3.  $\displaystyle \iint_\Sigma Pdydz$ ：投影到 $yOz$ 面，前侧为正、后侧为负，曲面垂直 $yOz$ 面时积分=0。

## 五、两类曲面积分的联系

 $\displaystyle \iint_\Sigma P dydz+Q dzdx+R dxdy=\iint_\Sigma (P\cos\alpha+Q\cos\beta+R\cos\gamma)dS$ 

其中 $\cos\alpha,\cos\beta,\cos\gamma$ 为有向曲面 $\Sigma$ 法向量的方向余弦。

# 第六节 高斯公式

## 一、高斯公式核心内容

设空间闭区域 $\Omega$ 由分片光滑的闭曲面 $\Sigma$ 围成，函数 $P,Q,R$ 在 $\Omega$ 上具有一阶连续偏导数，则：

 $\displaystyle \oiint_\Sigma P dydz+Q dzdx+R dxdy=\iiint_\Omega \big(\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}+\frac{\partial R}{\partial z}\big)dV$ 

**方向要求**： $\Sigma$ 为空间区域 $\Omega$ 的**外侧闭曲面**（内侧需加负号）。

## 二、通量与散度

**1. 通量定义**：设向量场 $\vec{F}=(P,Q,R)$ ， $\Sigma$ 为场内有向光滑曲面，则第二类曲面积分 $\displaystyle \iint_\Sigma \vec{F}\cdot d\vec{S}=\iint_\Sigma P dydz+Q dzdx+R dxdy$ ，称为向量场 $\vec{F}$ 穿过曲面 $\Sigma$ 的通量。

**2. 散度定义**：向量场 $\vec{F}=(P,Q,R)$ 的散度为 $div\vec{F}=\dfrac{\partial P}{\partial x}+\dfrac{\partial Q}{\partial y}+\dfrac{\partial R}{\partial z}$ ，高斯公式可简写为： $\displaystyle \oiint_\Sigma \vec{F}\cdot d\vec{S}=\iiint_\Omega div\vec{F} dV$ 。

## 三、核心解题应用

### 1. 闭曲面积分计算

直接将第二类闭曲面积分转化为三重积分，简化复杂曲面运算，是空间积分首选方法。

### 2. 非闭曲面补面法

开口曲面 $\Sigma$ 可补辅助面 $\Sigma_0$ 构成闭合曲面，用高斯公式求整体积分，再减去辅助面的积分值（辅助面多为坐标平面，积分极易计算）。

### 3. 求空间立体体积

令 $P=\dfrac{x}{3},Q=\dfrac{y}{3},R=\dfrac{z}{3}$ ，得体积公式： $\displaystyle V=\frac{1}{3}\oiint_\Sigma xdydz+ydzdx+zdxdy$ 。

## 四、易错要点

1. 适用前提： $P,Q,R$ 一阶偏导数连续，区域内无奇点；

2. 严格区分曲面内外侧，非外侧闭合曲面必须修正符号；

3. 补面时需保证补后曲面闭合，且统一曲面方向。

# 本章核心重难点总结

1. 区分核心：第一类积分（弧长、面积）**无方向、元素恒正**；第二类积分（坐标）**有方向、符号由方向决定**；

2. 定理层级：格林公式（平面曲线↔二重积分）、高斯公式（空间曲面积↔三重积分），是本章计算核心；

3. 解题思路：优先用定理转化积分，复杂题型用补线/补面法、挖奇点法简化运算。
