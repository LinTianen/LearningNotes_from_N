# 向量代数与空间解析几何
## 一、向量
### 1. 方向角与方向余弦
设向量 $\vec{a}=(x,y,z)$，模长 $|\vec{a}|=\sqrt{x^2+y^2+z^2}$，$\alpha,\beta,\gamma$ 为向量与 $x,y,z$ 轴正向的夹角（方向角）：
$$
\cos\alpha=\frac{x}{|\vec{a}|},\quad \cos\beta=\frac{y}{|\vec{a}|},\quad \cos\gamma=\frac{z}{|\vec{a}|}
$$
**重要恒等式**：
$$
\cos^2\alpha+\cos^2\beta+\cos^2\gamma=1
$$
$\{\cos\alpha,\cos\beta,\cos\gamma\}$ 是 $\vec{a}$ 同向单位向量。

### 2. 投影
向量 $\vec{a}$ 在 $\vec{b}$ 上的投影：
$$
\mathrm{Prj}_{\vec{b}}\vec{a}=|\vec{a}|\cos(\widehat{\vec{a},\vec{b}})=\frac{\vec{a}\cdot\vec{b}}{|\vec{b}|}
$$
投影运算性质：
1. $\mathrm{Prj}_{\vec{b}}(\vec{a}_1+\vec{a}_2)=\mathrm{Prj}_{\vec{b}}\vec{a}_1+\mathrm{Prj}_{\vec{b}}\vec{a}_2$
2. $\mathrm{Prj}_{\vec{b}}(\lambda\vec{a})=\lambda\,\mathrm{Prj}_{\vec{b}}\vec{a}$
### 3. 数量积
$$
\vec{a}\cdot\vec{b}=|\vec{a}||\vec{b}|\cos\theta=a_xb_x+a_yb_y+a_zb_z
$$
- 垂直判定：$\vec{a}\perp\vec{b} \iff \vec{a}\cdot\vec{b}=0$
- 夹角公式：$\cos\theta=\dfrac{\vec{a}\cdot\vec{b}}{|\vec{a}||\vec{b}|}$
### 4. 向量积（叉乘 $\vec{a}\times\vec{b}$）
设 $\vec{a}=(a_x,a_y,a_z),\ \vec{b}=(b_x,b_y,b_z)$
1. **模长几何意义**：$|\vec{a}\times\vec{b}|=|\vec{a}||\vec{b}|\sin\theta$，等于以 $\vec{a},\vec{b}$ 为邻边的平行四边形面积
2. **方向**：右手定则，$\vec{a}\times\vec{b}$ 同时垂直于 $\vec{a},\vec{b}$
3. **平行判定**：$\vec{a}\parallel\vec{b} \iff \vec{a}\times\vec{b}=\vec{0}$
4. **运算性质**
   - $\vec{a}\times\vec{a}=\vec{0}$
   - 反交换：$\vec{a}\times\vec{b}=-\vec{b}\times\vec{a}$
   - 数乘结合：$\lambda(\vec{a}\times\vec{b})=(\lambda\vec{a})\times\vec{b}=\vec{a}\times(\lambda\vec{b})$
   - 分配律：$(\vec{a}+\vec{b})\times\vec{c}=\vec{a}\times\vec{c}+\vec{b}\times\vec{c}$
5. **行列式计算公式**
$$
\vec{a}\times\vec{b}=
\begin{vmatrix}
\vec{i} & \vec{j} & \vec{k}\\
a_x & a_y & a_z\\
b_x & b_y & b_z
\end{vmatrix}
=(a_yb_z-a_zb_y,\ a_zb_x-a_xb_z,\ a_xb_y-a_yb_x)
$$

### 5. 混合积 $[\vec{a},\vec{b},\vec{c}]=(\vec{a}\times\vec{b})\cdot\vec{c}$
1. **几何意义**：绝对值 $|[\vec{a},\vec{b},\vec{c}]|$ = 以 $\vec{a},\vec{b},\vec{c}$ 为棱的平行六面体体积；符号判定右手系/左手系
2. **三向量共面判定**：$\vec{a},\vec{b},\vec{c}$ 共面 $\iff [\vec{a},\vec{b},\vec{c}]=0$
3. **轮换对称性**：
$$
[\vec{a},\vec{b},\vec{c}]=[\vec{b},\vec{c},\vec{a}]=[\vec{c},\vec{a},\vec{b}]
$$
互换任意两个向量，混合积变号
4. **行列式计算公式**
$$
[\vec{a},\vec{b},\vec{c}]=
\begin{vmatrix}
a_x & a_y & a_z\\
b_x & b_y & b_z\\
c_x & c_y & c_z
\end{vmatrix}
$$


## 二、空间直线与平面
### 1. 平面方程
1. **点法式**：过点 $M_0(x_0,y_0,z_0)$，法向量 $\vec{n}=(A,B,C)$
$$
A(x-x_0)+B(y-y_0)+C(z-z_0)=0
$$
2. **一般式**：$Ax+By+Cz+D=0$，法向量 $\vec{n}=(A,B,C)$
3. **截距式**：$\dfrac{x}{a}+\dfrac{y}{b}+\dfrac{z}{c}=1$（$a,b,c$ 为三坐标轴截距）

### 2. 空间直线方程
1. **一般式（两平面交线）**
$$
\begin{cases}
A_1x+B_1y+C_1z+D_1=0\\
A_2x+B_2y+C_2z+D_2=0
\end{cases}
$$
方向向量 $\vec{s}=\vec{n}_1\times\vec{n}_2$
2. **对称式（点向式）**：过 $M_0(x_0,y_0,z_0)$，方向向量 $\vec{s}=(m,n,p)$
$$
\frac{x-x_0}{m}=\frac{y-y_0}{n}=\frac{z-z_0}{p}
$$
3. **参数式**（令对称式等于 $t$）
$$
\begin{cases}
x=x_0+mt\\
y=y_0+nt\\
z=z_0+pt
\end{cases} \quad (t\in\mathbb{R})
$$
4. **三点式**
已知平面过 $M_1(x_1,y_1,z_1),M_2(x_2,y_2,z_2),M_3(x_3,y_3,z_3)$
$$
\begin{vmatrix}
x-x_1 & y-y_1 & z-z_1 \\
x_2-x_1 & y_2-y_1 & z_2-z_1 \\
x_3-x_1 & y_3-y_1 & z_3-z_1
\end{vmatrix}=0
$$
5. **截距式**
平面在 $x,y,z$ 轴截距分别为 $a,b,c\ (a,b,c\neq0)$
$$
\frac{x}{a}+\frac{y}{b}+\frac{z}{c}=1
$$
### 3. 位置关系公式
1. 两平面夹角：法向量夹角；两直线夹角：方向向量夹角；线面夹角：直线方向向量与平面法向量夹角的余角
2. 点到平面距离：$M_1(x_1,y_1,z_1)$ 到 $Ax+By+Cz+D=0$
$$
d=\frac{|Ax_1+By_1+Cz_1+D|}{\sqrt{A^2+B^2+C^2}}
$$
3. 点到直线距离
    直线过点 $M_0$，方向向量 $\vec{s}$，空间定点 $M$
    $$
    d=\frac{|\overrightarrow{M_0M}\times\vec{s}|}{|\vec{s}|}
    $$


## 三、曲面
### 1. 旋转曲面
**口诀**：绕哪个坐标轴旋转，该坐标轴对应坐标不变；另一组坐标替换为 $\pm\sqrt{\text{另外两坐标平方和}}$
例：$xOz$ 平面曲线 $f(x,z)=0$
- 绕 $x$ 轴旋转：$f(x,\pm\sqrt{y^2+z^2})=0$
- 绕 $z$ 轴旋转：$f(\pm\sqrt{x^2+y^2},z)=0$

### 2. 柱面
方程缺哪个变量，柱面母线平行于该坐标轴
- $F(x,y)=0$：母线平行 $z$ 轴
- $G(x,z)=0$：母线平行 $y$ 轴
- $H(y,z)=0$：母线平行 $x$ 轴

### 3. 椭球面
$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}=1
$$
$a,b,c$ 为三个半轴长；$a=b=c$ 时为球面 $x^2+y^2+z^2=R^2$

### 4. 抛物面
1. **椭圆抛物面**
$$
\frac{x^2}{2p}+\frac{y^2}{2q}=z \quad (p,q>0，开口向上)
$$
2. **双曲抛物面（马鞍面）**
$$
\frac{x^2}{-2p}+\frac{y^2}{2q}=z \quad (p,q>0)
$$

### 5. 双曲面
1. **单叶双曲面**（一处贯通）
$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}-\frac{z^2}{c^2}=1
$$
2. **双叶双曲面**（分成两部分）
$$
\frac{x^2}{a^2}-\frac{y^2}{b^2}-\frac{z^2}{c^2}=1
$$

### 6. 二次锥面（椭圆锥面）
$$
\frac{x^2}{a^2}+\frac{y^2}{b^2}=z^2
$$
$a=b$ 时为圆锥面 $x^2+y^2=k^2z^2$

---

## 四、空间曲线
### 1. 一般式（两曲面交线）
$$
C:\ \begin{cases}
F(x,y,z)=0\\
G(x,y,z)=0
\end{cases}
$$

### 2. 参数方程
以参数 $t$ 表示三个坐标：
$$
\begin{cases}
x=x(t)\\
y=y(t)\\
z=z(t)
\end{cases} \quad t\in[\alpha,\beta]
$$

### 3. 空间曲线在坐标面上的投影曲线
以 $xOy$ 平面投影举例：
1. 联立曲线方程 $\begin{cases}F(x,y,z)=0\\G(x,y,z)=0\end{cases}$，消去变量 $z$，得**投影柱面** $H(x,y)=0$
2. 联立投影柱面与坐标面 $z=0$，得到**投影曲线**
$$
\begin{cases}
H(x,y)=0\\
z=0
\end{cases}
$$
同理：
- $xOz$ 投影：消 $y$，联立 $\begin{cases}\varPhi(x,z)=0\\y=0\end{cases}$
- $yOz$ 投影：消 $x$，联立 $\begin{cases}\Psi(y,z)=0\\x=0\end{cases}$
