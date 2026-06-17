# 重积分

# 一、二重积分的概念与性质

## （一）二重积分的定义

设二元函数  $f(x,y)$  定义在平面有界闭区域  $D$  上，将区域  $D$  任意划分为  $n$  个小闭区域  $\Delta \sigma_i$ （ $i=1,2,...,n$ ）， $\Delta \sigma_i$  同时表示小区域的面积。在每个小区域内任取一点  $(\xi_i,\eta_i)$ ，作和式  $\displaystyle \sum_{i=1}^n f(\xi_i,\eta_i)\Delta \sigma_i$ 。

令  $\lambda$  为所有小区域直径的最大值，若当  $\lambda \to 0$  时，上述和式极限存在且与区域划分方式、取点方式无关，则称函数  $f(x,y)$  在区域  $D$  上可积，该极限为 **二重积分**，记作：

 $\displaystyle \iint_D f(x,y)d\sigma=\lim\limits_{\lambda \to 0}\sum_{i=1}^n f(\xi_i,\eta_i)\Delta \sigma_i$ 

其中： $f(x,y)$ 为被积函数， $d\sigma$  为面积元素， $D$  为积分区域。

## （二）几何意义与物理意义

**1. 几何意义**：当  $f(x,y)\geq0$  时，二重积分表示以曲面  $z=f(x,y)$  为顶、积分区域  $D$  为底的**曲顶柱体的体积**；若  $f(x,y)<0$ ，积分值为体积的相反数；若函数有正有负，积分值为区域上正负体积的代数和。

**2. 物理意义**：若平面薄片的面密度为  $\rho(x,y)$ ，则二重积分  $\displaystyle \iint_D \rho(x,y)d\sigma$  表示该平面薄片的**质量**。

## （三）二重积分的核心性质

默认  $f(x,y)、g(x,y)$  在闭区域  $D$  上可积， $k$  为常数。

**1. 线性性质**

 $\displaystyle \iint_D [k_1f(x,y)\pm k_2g(x,y)]d\sigma=k_1\iint_D f(x,y)d\sigma \pm k_2\iint_D g(x,y)d\sigma$ 

**2. 区域可加性**

若积分区域  $D=D_1+D_2$ （ $D_1、D_2$  无重叠内部区域），则：

 $\displaystyle \iint_D f(x,y)d\sigma=\iint_{D_1} f(x,y)d\sigma+\iint_{D_2} f(x,y)d\sigma$ 

**3. 保号性**

若在区域  $D$  上  $f(x,y)\geq0$ ，则  $\displaystyle \iint_D f(x,y)d\sigma\geq0$ ；若  $f(x,y)\geq g(x,y)$ ，则  $\displaystyle \iint_D f(x,y)d\sigma\geq \iint_D g(x,y)d\sigma$ 。

**4. 估值定理**

设  $M、m$  分别为  $f(x,y)$  在  $D$ 上的最大值、最小值， $\sigma$  为区域  $D$  的面积，则：

 $\displaystyle m\sigma \leq \iint_D f(x,y)d\sigma \leq M\sigma$ 

**5. 积分中值定理**

若  $f(x,y)$  在闭区域  $D$  上连续，则存在一点  $(\xi,\eta)\in D$ ，使得：

 $\displaystyle \iint_D f(x,y)d\sigma=f(\xi,\eta)\cdot\sigma$ 

**6. 对称性性质（高频考点）**

- 若区域  $D$  关于 $x$  轴对称： $f(x,y)$  关于  $y$  为奇函数（ $f(x,-y)=-f(x,y)$ ），积分值为0；为偶函数（ $f(x,-y)=f(x,y)$ ），积分值为2倍上半区域积分。

- 若区域  $D$  关于  $y$  轴对称： $f(x,y)$  关于  $x$  为奇函数（ $f(-x,y)=-f(x,y)$ ），积分值为0；为偶函数，积分值为2倍右半区域积分。

- 若区域  $D$  关于原点对称： $f(-x,-y)=-f(x,y)$  积分值为0； $f(-x,-y)=f(x,y)$ ，积分值为4倍第一象限区域积分。

# 二、二重积分的计算法

二重积分的核心计算思路：**转化为两次定积分（累次积分）计算**，主要分为直角坐标、极坐标两种计算方法，根据积分区域和被积函数形式选择。

## （一）直角坐标下的计算

### 1. X型区域（先y后x积分）

区域形式： $D: a\leq x\leq b,\ \varphi_1(x)\leq y\leq \varphi_2(x)$ （区域由两条竖线、两条曲线围成）

积分公式： $\displaystyle \iint_D f(x,y)d\sigma=\int_a^b dx \int_{\varphi_1(x)}^{\varphi_2(x)} f(x,y)dy$ 

### 2. Y型区域（先x后y积分）

区域形式： $D: c\leq y\leq d,\ \psi_1(y)\leq x\leq \psi_2(y)$ （区域由两条横线、两条曲线围成）

积分公式： $\displaystyle \iint_D f(x,y)d\sigma=\int_c^d dy \int_{\psi_1(y)}^{\psi_2(y)} f(x,y)dx$ 

### 3. 积分次序交换原则

复杂区域需拆分区域、交换积分次序，步骤：①根据累次积分还原积分区域；②画出区域草图；③重新确定变量范围，改写累次积分。多用于无法直接积分的函数（如  $e^{x^2}、\frac{\sin x}{x}$ ）。

## （二）极坐标下的计算

### 1. 坐标转换公式

直角坐标转极坐标： $x=\rho\cos\theta,\ y=\rho\sin\theta$ ，面积元素 $d\sigma=\rho d\rho d\theta$ 

二重积分转换公式： $\displaystyle \iint_D f(x,y)d\sigma=\iint_D f(\rho\cos\theta,\rho\sin\theta)\rho d\rho d\theta$ 

### 2. 适用场景

1. 积分区域为圆、圆环、扇形、心形线等极坐标规则图形；
2. 被积函数含  $\displaystyle x^2+y^2、\frac{y}{x}、\arctan\frac{y}{x}$  等形式。

### 3. 常见极坐标区域类型

- 极点在区域内部： $0\leq \theta\leq 2\pi,\ 0\leq \rho\leq \rho(\theta)$ 

- 极点在区域边界： $\alpha\leq \theta\leq \beta,\ 0\leq \rho\leq \rho(\theta)$ 

- 极点在区域外部： $\alpha\leq \theta\leq \beta,\ \rho_1(\theta)\leq \rho\leq \rho_2(\theta)$ 

# 三、三重积分

## （一）三重积分的概念

设三元函数  $f(x,y,z)$  定义在空间有界闭区域  $\Omega$  上，通过分割、取点、求和、取极限，可得三重积分定义：

 $\displaystyle \iiint_\Omega f(x,y,z)dV=\lim\limits_{\lambda \to 0}\sum_{i=1}^n f(\xi_i,\eta_i,\zeta_i)\Delta V_i$ 

其中  $dV$  为体积元素，几何意义： $f(x,y,z)=1$  时，积分值为空间区域  $\Omega$  的体积；物理意义：表示空间物体的质量（ $f$  为体密度）。

三重积分继承二重积分的**线性、区域可加性、保号性、中值定理、对称性**，规律一致。

## （二）三重积分的三种计算方法

### 1. 直角坐标计算

**（1）投影法（先一后二）**：先对  $z$  积分，再对平面区域  $D_{xy}$  做二重积分

区域形式： $\Omega: (x,y)\in D_{xy},\ z_1(x,y)\leq z\leq z_2(x,y)$ 

公式： $\displaystyle \iiint_\Omega f(x,y,z)dV=\iint_{D_{xy}} dxdy \int_{z_1(x,y)}^{z_2(x,y)} f(x,y,z)dz$ 

**（2）截面法（先二后一）**：适合被积函数仅含  $z$ 、截面面积易求的场景

区域形式： $\Omega: c_1\leq z\leq c_2,\ (x,y)\in D_z$ 

公式： $\displaystyle \iiint_\Omega f(x,y,z)dV=\int_{c_1}^{c_2} dz \iint_{D_z} f(x,y,z)dxdy$ 

### 2. 柱面坐标计算

**（1）坐标转换**： $x=\rho\cos\theta,\ y=\rho\sin\theta,\ z=z$ ，体积元素  $dV=\rho d\rho d\theta dz$ 

**（2）适用场景**：积分区域含圆柱、旋转抛物面，被积函数含  $x^2+y^2$ 。

**（3）积分公式**： $\displaystyle \iiint_\Omega f(x,y,z)dV=\iiint_\Omega f(\rho\cos\theta,\rho\sin\theta,z)\rho d\rho d\theta dz$ 

### 3. 球面坐标计算

**（1）坐标转换**： $x=r\sin\varphi\cos\theta,\ y=r\sin\varphi\sin\theta,\ z=r\cos\varphi$ ，体积元素  $dV=r^2\sin\varphi drd\varphi d\theta$ 

参数含义： $r$  为原点到点的距离， $\varphi$  为极角（与z轴夹角）， $\theta$  为方位角。

**（2）适用场景**：积分区域为球体、球壳、圆锥体，被积函数含  $x^2+y^2+z^2$ 。

# 四、重积分的应用

## （一）几何应用

### 1. 平面图形面积

区域  $D$  的面积： $\displaystyle \sigma=\iint_D 1\cdot d\sigma$ 

### 2. 空间几何体体积

- 曲顶柱体体积： $\displaystyle V=\iint_D f(x,y)d\sigma\ (f(x,y)\geq0)$ 

- 空间闭区域体积： $\displaystyle V=\iiint_\Omega 1\cdot dV$ 

### 3. 曲面面积

若曲面方程为  $z=z(x,y)$ ，投影区域为  $D_{xy}$ ，则曲面面积：

 $\displaystyle S=\iint_{D_{xy}} \sqrt{1+(\frac{\partial z}{\partial x})^2+(\frac{\partial z}{\partial y})^2}dxdy$ 

## （二）核心解题技巧总结

1. 优先利用**对称性、奇偶性**化简积分，大幅减少计算量；

2. 二重积分优先判断直角/极坐标，三重积分优先判断直角/柱面/球面坐标；

3. 遇积不出的函数（ $e^{x^2}、\sin x^2$ ），必须交换二重积分次序；

4. 物理应用类题目，熟记公式，区分平面与空间、质心与转动惯量的公式差异。
