# 多元函数微分学（高数第九章）
## 一、极限与连续
### 1. 二重极限
设 $z=f(x,y)$ 在 $P_0(x_0,y_0)$ 的某去心邻域内有定义，$P_0$ 是定义域 $D$ 的聚点。若存在常数 $A$，对任意 $\varepsilon>0$，总存在 $\delta>0$，当 $0<|PP_0|<\delta$ 时，恒有 $|f(P)-A|<\varepsilon$，则称
$$\lim_{(x,y)\to(x_0,y_0)} f(x,y) = A$$
- 核心特点：动点 $(x,y)$ 须以**任意路径**趋近于 $P_0$ 时极限都相等；沿不同路径极限不同则极限不存在。
- 常用判别法：极坐标代换，将二元极限转化为一元函数极限判断。

### 2. 连续
若 $z=f(x,y)$ 在 $P_0(x_0,y_0)$ 的某邻域内有定义，且
$$\lim_{(x,y)\to(x_0,y_0)} f(x,y) = f(x_0,y_0)$$
则称 $f(x,y)$ 在点 $P_0$ 处连续；若在区域 $D$ 内每一点都连续，则称函数在 $D$ 上连续。
- 性质：**多元初等函数在其定义域内连续**。

### 3. 有界闭区域上连续函数的性质
1. 有界性：函数在有界闭区域上有界
2. 最值定理：必能取得最大值和最小值
3. 介值定理：介于两个函数值之间的数必能取到
4. 一致连续性

---

## 二、偏导数
### 1. 定义
设 $z=f(x,y)$ 在 $(x_0,y_0)$ 某邻域内有定义，若极限
$$\lim_{\Delta x\to0} \frac{f(x_0+\Delta x,\,y_0) - f(x_0,y_0)}{\Delta x}$$
存在，则称其为 $f(x,y)$ 在 $(x_0,y_0)$ 处对 $x$ 的偏导数，记作
$$f_x(x_0,y_0),\quad \left.\frac{\partial z}{\partial x}\right|_{(x_0,y_0)}$$

### 2. 几何意义
$f_x(x_0,y_0)$ 表示曲面 $z=f(x,y)$ 被平面 $y=y_0$ 截得的曲线，在点 $(x_0,y_0,f(x_0,y_0))$ 处的切线对 $x$ 轴的斜率。

### 3. 偏导存在与连续的关系
**偏导数存在 ≠ 函数连续，函数连续 ≠ 偏导数存在**，二者无必然推导关系。

### 4. 混合偏导相等定理
若二阶混合偏导数 $f_{xy}$ 和 $f_{yx}$ 在区域 $D$ 内连续，则在 $D$ 内恒有 $f_{xy}=f_{yx}$。

---

## 三、全微分
### 1. 定义
设 $z=f(x,y)$ 在点 $(x,y)$ 的全增量
$$\Delta z = f(x+\Delta x,\,y+\Delta y) - f(x,y)$$
可表示为
$$\Delta z = A\Delta x + B\Delta y + o(\rho),\quad \rho=\sqrt{(\Delta x)^2+(\Delta y)^2}$$
则称函数在该点可微，全微分为 $dz = A\Delta x + B\Delta y$。

### 2. 必要条件
若 $z=f(x,y)$ 在 $(x,y)$ 处可微，则该点偏导数必存在，且
$$dz = f_x(x,y)dx + f_y(x,y)dy$$

### 3. 充分条件
若 $z=f(x,y)$ 的偏导数 $f_x,f_y$ 在点 $(x,y)$ 处连续，则函数在该点可微。

### 4. 概念推导关系
$$\text{偏导数连续} \implies \text{可微} \implies \begin{cases}
\text{函数连续} \\
\text{偏导数存在}
\end{cases}$$
反向推导均不成立。

---

## 四、复合函数求导法则
### 1. 一元中间变量（全导数）
设 $z=f(u,v)$，$u=u(t),\ v=v(t)$，则
$$\frac{dz}{dt} = \frac{\partial z}{\partial u}\cdot\frac{du}{dt} + \frac{\partial z}{\partial v}\cdot\frac{dv}{dt}$$

### 2. 多元中间变量
设 $z=f(u,v)$，$u=u(x,y),\ v=v(x,y)$，则
$$
\frac{\partial z}{\partial x} = \frac{\partial z}{\partial u}\cdot\frac{\partial u}{\partial x} + \frac{\partial z}{\partial v}\cdot\frac{\partial v}{\partial x}
$$
$$
\frac{\partial z}{\partial y} = \frac{\partial z}{\partial u}\cdot\frac{\partial u}{\partial y} + \frac{\partial z}{\partial v}\cdot\frac{\partial v}{\partial y}
$$

### 补充：全微分形式不变性
无论 $u,v$ 是自变量还是中间变量，函数 $z=f(u,v)$ 的全微分形式始终为
$$dz = \frac{\partial z}{\partial u}du + \frac{\partial z}{\partial v}dv$$

---

## 五、隐函数求导
### 1. 一元隐函数存在定理
**条件**：$F(x,y)$ 在点 $P_0(x_0,y_0)$ 某邻域内有连续一阶偏导数；$F(x_0,y_0)=0$；$F_y(x_0,y_0)\neq0$
**结论**：邻域内唯一确定连续可导函数 $y=f(x)$，满足 $y_0=f(x_0)$，且
$$\frac{dy}{dx} = -\frac{F_x}{F_y}$$

### 2. 二元隐函数存在定理
**条件**：$F(x,y,z)$ 在点 $P_0(x_0,y_0,z_0)$ 某邻域内有连续一阶偏导数；$F(x_0,y_0,z_0)=0$；$F_z(x_0,y_0,z_0)\neq0$
**结论**：邻域内唯一确定连续可导函数 $z=f(x,y)$，满足 $z_0=f(x_0,y_0)$，且
$$\frac{\partial z}{\partial x} = -\frac{F_x}{F_z},\quad \frac{\partial z}{\partial y} = -\frac{F_y}{F_z}$$

### 3. 隐函数组定理
设方程组 $\begin{cases}F(x,y,u,v)=0 \\ G(x,y,u,v)=0\end{cases}$，雅可比行列式
$$J = \frac{\partial(F,G)}{\partial(u,v)} = \begin{vmatrix}F_u & F_v \\ G_u & G_v\end{vmatrix}$$
若 $J$ 在点 $P$ 处不为0，则可确定隐函数 $u=u(x,y),\ v=v(x,y)$，偏导公式：
$$\frac{\partial u}{\partial x} = -\frac{1}{J}\cdot\frac{\partial(F,G)}{\partial(x,v)},\quad \frac{\partial v}{\partial x} = -\frac{1}{J}\cdot\frac{\partial(F,G)}{\partial(u,x)}$$
对 $y$ 的偏导同理替换即可。

---

## 六、微分学的几何应用
### 1. 空间参数曲线
曲线 $\Gamma: \begin{cases}x=x(t) \\ y=y(t) \\ z=z(t)\end{cases}$，对应参数 $t_0$ 的点 $M_0(x_0,y_0,z_0)$
- 切向量：$\vec{T} = \big(x'(t_0),\ y'(t_0),\ z'(t_0)\big)$
- 切线方程：$\displaystyle \frac{x-x_0}{x'(t_0)} = \frac{y-y_0}{y'(t_0)} = \frac{z-z_0}{z'(t_0)}$
- 法平面方程：$x'(t_0)(x-x_0) + y'(t_0)(y-y_0) + z'(t_0)(z-z_0) = 0$

### 2. 空间一般式曲线（两曲面交线）
曲线 $\begin{cases}F(x,y,z)=0 \\ G(x,y,z)=0\end{cases}$，切向量为两曲面法向量的叉乘
$$\vec{T} = \nabla F \times \nabla G = \begin{vmatrix}
\vec{i} & \vec{j} & \vec{k} \\
F_x & F_y & F_z \\
G_x & G_y & G_z
\end{vmatrix}$$

### 3. 曲面 $F(x,y,z)=0$
点 $M_0(x_0,y_0,z_0)$ 在曲面上
- 法向量：$\vec{n} = \big(F_x(M_0),\ F_y(M_0),\ F_z(M_0)\big)$
- 切平面方程：$F_x(M_0)(x-x_0) + F_y(M_0)(y-y_0) + F_z(M_0)(z-z_0) = 0$
- 法线方程：$\displaystyle \frac{x-x_0}{F_x(M_0)} = \frac{y-y_0}{F_y(M_0)} = \frac{z-z_0}{F_z(M_0)}$

### 4. 显式曲面与参数曲面
- 显式曲面 $z=f(x,y)$：令 $F(x,y,z)=f(x,y)-z$，法向量 $\vec{n}=(f_x,\ f_y,\ -1)$
- 参数曲面 $\vec{r}=\vec{r}(u,v)$：法向量 $\vec{n} = \vec{r}_u \times \vec{r}_v$

---

## 七、方向导数与梯度
### 1. 方向导数定义
函数沿指定方向 $\vec{l}$ 的瞬时变化率
$$\left.\frac{\partial f}{\partial l}\right|_{P_0} = \lim_{t\to0^+} \frac{f(x_0+t\cos\alpha,\, y_0+t\cos\beta) - f(x_0,y_0)}{t}$$
其中 $\cos\alpha,\cos\beta$ 为方向 $\vec{l}$ 的方向余弦。

### 2. 可微条件下计算公式
$$\frac{\partial f}{\partial l} = f_x \cos\alpha + f_y \cos\beta$$
三维情形补充 $f_z\cos\gamma$ 项。

### 3. 梯度
- 定义：$\displaystyle \mathrm{grad}\,f(x_0,y_0) = \nabla f(x_0,y_0) = \big(f_x(x_0,y_0),\ f_y(x_0,y_0)\big)$
- 与方向导数的关系：$\displaystyle \frac{\partial f}{\partial l} = \nabla f \cdot \vec{e}_l = |\nabla f| \cos\theta$
- 核心性质：**梯度方向是方向导数取得最大值的方向，梯度的模为最大方向导数值**。

---

## 八、多元函数的极值与最值
### 1. 极值存在的必要条件
若 $f(x,y)$ 在 $(x_0,y_0)$ 处偏导数存在且取得极值，则
$$f_x(x_0,y_0)=0,\quad f_y(x_0,y_0)=0$$
满足该式的点称为驻点；**驻点不一定是极值点**。

### 2. 极值的充分条件
设 $z=f(x,y)$ 在 $(x_0,y_0)$ 某邻域内有二阶连续偏导数，且 $(x_0,y_0)$ 为驻点，记
$$A=f_{xx}(x_0,y_0),\quad B=f_{xy}(x_0,y_0),\quad C=f_{yy}(x_0,y_0)$$
- 若 $AC-B^2>0$：有极值，$A>0$ 为极小值，$A<0$ 为极大值
- 若 $AC-B^2<0$：无极值
- 若 $AC-B^2=0$：无法判定，需另行讨论

### 3. 有界闭区域上求最值步骤
1. 求区域内部所有可能极值点（驻点、偏导数不存在的点）
2. 求区域边界上的极值
3. 比较所有点的函数值，最大为最大值，最小为最小值

### 4. 条件极值：拉格朗日乘数法
目标函数 $f(x,y)$，约束条件 $\varphi(x,y)=0$，构造拉格朗日函数
$$L(x,y,\lambda) = f(x,y) + \lambda\varphi(x,y)$$
令各偏导数为0，解方程组得可能极值点：
$$
\begin{cases}
L_x = f_x + \lambda\varphi_x = 0 \\
L_y = f_y + \lambda\varphi_y = 0 \\
L_\lambda = \varphi(x,y) = 0
\end{cases}
$$
多变量、多约束情形可按同理推广。
