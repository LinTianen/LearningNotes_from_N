# 无穷级数

# 一、常数项级数的概念和性质

## 1.1 基本概念

### （1）常数项级数定义

由无穷多个常数构成的表达式  $\displaystyle \sum_{n=1}^{\infty} u_n = u_1+u_2+u_3+\dots+u_n+\dots$ 称为**常数项无穷级数**，简称常数项级数，其中  $u_n$  为级数的一般项。

### （2）部分和与敛散性

取级数前  $n$  项和  $\displaystyle S_n = \sum_{k=1}^{n} u_k = u_1+u_2+\dots+u_n$ ，称  $\{S_n\}$  为级数的**部分和数列**。

- **收敛**：若  $\lim\limits_{n \to \infty} S_n = S$ （ $S$  为有限常数），则称级数  $\displaystyle \sum_{n=1}^{\infty} u_n$  收敛， $S$  为级数的和，即  $\displaystyle \sum_{n=1}^{\infty} u_n = S$ 。

- **发散**：若  $\lim\limits_{n \to \infty} S_n$  不存在（或为无穷大），则称级数发散，发散级数无和。

- **余项**：收敛级数的余项  $r_n = S - S_n = \displaystyle \sum_{k=n+1}^{\infty} u_k$ ，满足  $\lim\limits_{n \to \infty} r_n = 0$ 

### （3）两个基础经典级数

- **几何级数（等比级数）**： $\displaystyle \sum_{n=0}^{\infty} aq^n = a+aq+aq^2+\dots$ （ $a \neq 0$ ）
敛散性： $|q| < 1$  时收敛，和为  $\displaystyle \frac{a}{1-q}$ ； $|q| \geq 1$  时发散

- **调和级数**： $\displaystyle \sum_{n=1}^{\infty} \frac{1}{n} = 1+\frac{1}{2}+\frac{1}{3}+\dots$ ，**恒发散**

## 1.2 常数项级数的基本性质

1. **数乘性**：级数  $\sum u_n$  收敛于  $S$ ，则  $\sum ku_n$  收敛于  $kS$ （ $k$  为常数）； $k \neq 0$  时， $\sum u_n$  与  $\sum ku_n$  敛散性一致。

2. **加减性**：若  $\sum u_n$ 、 $\sum v_n$ 分别收敛于  $S、T$ ，则  $\sum (u_n \pm v_n)$  收敛于  $S \pm T$ 。
- 推论：收敛+发散=发散；发散+发散=敛散性不确定。

3. **有限项不变性**：增减、改变级数的**有限项**，不改变级数的敛散性（仅收敛级数的和会改变）。

4. **结合性**：收敛级数任意加括号后得到的新级数仍收敛，且和不变。
- 推论：加括号后的级数发散，则原级数一定发散；加括号收敛，原级数不一定收敛。

5. **收敛必要条件**：若  $\displaystyle \sum_{n=1}^{\infty} u_n$  收敛，则  $\lim\limits_{n \to \infty} u_n = 0$ 。
⚠️ 易错点： $\lim u_n=0$  是收敛**必要不充分条件**（如调和级数通项趋于0，但发散）；若  $\lim u_n \neq 0$ ，级数必发散（常用判散方法）。

# 二、常数项级数的审敛法

常数项级数分为正项级数、交错级数、任意项级数，三类级数对应不同审敛法则，是级数敛散性判断的核心考点。

## 2.1 正项级数审敛法（ $u_n \geq 0$ ）

正项级数核心特征：部分和数列  $\{S_n\}$  单调递增，因此正项级数收敛  $\iff \{S_n\}$  有上界。

### （1）比较审敛法

基本形式：设  $0 \leq u_n \leq v_n$ ，则 

1.  $\sum v_n$  收敛  $\Rightarrow \sum u_n$  收敛；

2.  $\sum u_n$  发散  $\Rightarrow \sum v_n$  发散。

极限形式（常用）：设  $u_n,v_n > 0$ ， $\lim\limits_{n \to \infty} \dfrac{u_n}{v_n} = l$ ，则：

-  $0 < l < +\infty$ ：两级数**同敛散**；

-  $l=0$ ： $\sum v_n$  收敛  $\Rightarrow \sum u_n$  收敛；

-  $l=+\infty$ ： $\sum v_n$  发散  $\Rightarrow \sum u_n$  发散。

常用比较基准级数：

1. **几何级数（等比级数）** $\displaystyle \sum_{n=0}^{\infty} aq^n$ （ $|q| < 1$  时收敛， $|q| \geq 1$  时发散）

2. **p-级数** $\displaystyle \sum_{n=1}^{\infty} \frac{1}{n^p}$ （ $p>1$  收敛， $p \leq 1$  发散）。

### （2）比值审敛法（达朗贝尔判别法）

设正项级数  $\sum u_n$ ， $\lim\limits_{n \to \infty} \dfrac{u_{n+1}}{u_n} = \rho$ ，则：

-  $\rho < 1$ ：级数收敛；

-  $\rho > 1$ （含 $\infty$ ）：级数发散；

-  $\rho = 1$ ：判别失效（需改用比较审敛法，如p-级数）。

适用场景：通项含阶乘、指数幂（ $n!、2^n、3^n$ ）的级数。

### （3）根值审敛法（柯西判别法）

设正项级数  $\sum u_n$ ， $\lim\limits_{n \to \infty} \sqrt[n]{u_n} = \rho$ ，敛散性结论同比值审敛法。

适用场景：通项含  $n$  次幂的级数。

## 2.2 交错级数审敛法

交错级数定义：正负项交替出现的级数，标准形式  $\displaystyle \sum_{n=1}^{\infty} (-1)^{n-1} u_n$ （ $u_n > 0$ ）。

**莱布尼茨判别准则**：若交错级数满足两个条件：

1.  $u_n \geq u_{n+1}$ （数列单调递减）

2.  $\lim\limits_{n \to \infty} u_n = 0$ ，则级数收敛，且余项  $|r_n| \leq u_{n+1}$ 。

⚠️ 注意：两个条件缺一不可，仅通项趋于0无法判定交错级数收敛。

## 2.3 任意项级数审敛法

任意项级数：通项  $u_n$  可正、可负、可为0的常数项级数。

### （1）绝对收敛与条件收敛

- 绝对收敛：若  $\displaystyle \sum_{n=1}^{\infty} |u_n|$  收敛，则  $\sum u_n$  绝对收敛（绝对收敛的级数一定收敛）；

- 条件收敛：若  $\sum |u_n|$  发散，但  $\sum u_n$  收敛，则级数条件收敛。

> 绝对收敛级数可任意重排项的顺序，和不变；条件收敛级数重排后可能改变敛散性或和。
> 
> 

# 三、幂级数

## 3.1 幂级数基本定义

1. 函数项级数：通项为函数的级数  $\displaystyle \sum_{n=0}^{\infty} u_n(x)$ ；

2. 幂级数标准形式： $\displaystyle \sum_{n=0}^{\infty} a_n x^n = a_0+a_1x+a_2x^2+\dots$ （ $a_n$  为常数，称系数）；

3. 一般形式： $\displaystyle \sum_{n=0}^{\infty} a_n (x-x_0)^n$ （中心点为  $x_0$ ）。

## 3.2 阿贝尔定理（幂级数核心定理）

1. 若幂级数在  $x=x_0 \neq 0$  处收敛，则对所有满足  $|x| < |x_0|$  的  $x$ ，级数**绝对收敛**；

2. 若幂级数在 $x=x_1$  处发散，则对所有满足  $|x| > |x_1|$  的  $x$ ，级数**发散**。

推论：幂级数的收敛域必为区间，存在**收敛半径** $R$ ：

-  $|x| < R$ ：级数绝对收敛；

-  $|x| > R$ ：级数发散；

-  $x=\pm R$ ：需单独判断敛散性。

## 3.3 收敛半径与收敛域求解

### （1）收敛半径公式

对幂级数  $\sum a_n x^n$ ，若  $\lim\limits_{n \to \infty} \left|\dfrac{a_{n+1}}{a_n}\right| = \rho$ ，则 $R = \begin{cases} \dfrac{1}{\rho}, & \rho \neq 0 \\ +\infty, & \rho=0 \\ 0, & \rho=+\infty \end{cases}$ 

也可由根值法  $\lim\limits_{n \to \infty} \sqrt[n]{|a_n|}=\rho$  求解  $R$ 。

### （2）收敛域求解步骤

第一步：求收敛半径  $R$ ，得开区间  $(-R,R)$ ；第二步：单独判断端点  $x=\pm R$  处的敛散性；第三步：整合得到完整收敛域。

## 3.4 幂级数的运算性质

设幂级数  $\sum a_n x^n=S(x)$ 、 $\sum b_n x^n=T(x)$ ，收敛半径分别为  $R_1、R_2$ ，取  $R=\min\{R_1,R_2\}$ 。

### （1）四则运算

在  $(-R,R)$  内，级数可逐项加减、相乘，和函数连续。

### （2）逐项求导（保收敛性）

 $S'(x) = \displaystyle\sum_{n=1}^{\infty} n a_n x^{n-1}$ ，收敛半径不变，端点敛散性可能改变。

### （3）逐项积分（保收敛性）

 $\displaystyle\int_{0}^{x} S(t)dt = \sum_{n=0}^{\infty} \frac{a_n}{n+1} x^{n+1}$ ，收敛半径不变，端点敛散性可能改变。

核心用途：通过逐项求导、积分将复杂幂级数转化为几何级数，求和后再还原，求解和函数。

# 四、函数展开成幂级数

## 4.1 泰勒级数与麦克劳林级数

### （1）泰勒公式

若函数  $f(x)$  在  $x_0$  邻域内任意阶可导，则  $\displaystyle f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n$ ，称为  $f(x)$  在  $x_0$  处的**泰勒级数**。

### （2）麦克劳林级数

当  $x_0=0$  时，泰勒级数简化为  $\displaystyle f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!}x^n$ ，是最常用的幂级数展开形式。

### （3）展开充要条件

函数  $f(x)$  在区间内能展开为泰勒级数  $\iff$ 泰勒公式余项  $\lim\limits_{n \to \infty} R_n(x)=0$ 。

## 4.2 常用初等函数麦克劳林展开式（必背）
[速记技巧](./常用麦克劳林公式记忆技巧大全（无痛背诵、考场通用）.md)
1.  $\displaystyle e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!}$ ， $x \in (-\infty,+\infty)$ 

2.  $\displaystyle \sin x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{(2n+1)!}$ ， $x \in (-\infty,+\infty)$ 

3.  $\displaystyle \frac{1}{1+x} = \sum_{n=0}^{\infty} (-1)^n x^n$ ， $x \in (-1,1)$ 

4.  $\displaystyle \ln(1+x) = \sum_{n=1}^{\infty} \frac{(-1)^{n-1} x^n}{n}$ ， $x \in (-1,1]$ 

    > 利用导数关系  $\displaystyle [\ln(1+x)]'=\frac{1}{1+x}$ ，对  $\displaystyle \frac{1}{1+x}$  的幂级数在区间  $[0,x]$  上逐项积分： $\displaystyle \int_{0}^{x}\frac{1}{1+t}\mathrm{d}t=\int_{0}^{x}\sum\limits_{n=0}^{\infty}(-1)^n t^n\mathrm{d}t$ ，交换积分与求和顺序，计算得  $\displaystyle \ln(1+x)=\sum\limits_{n=1}^{\infty} \frac{(-1)^{n-1} x^n}{n}$ 。

5.  $\displaystyle a^x = \sum_{n=0}^{\infty} \frac{(x\ln a)^n}{n!}$ ， $x \in (-\infty,+\infty)$ 

6.  $\displaystyle \frac{1}{1-x} = \sum_{n=0}^{\infty} x^n$ ， $x \in (-1,1)$ 

7.  $\displaystyle \frac{1}{1+x^2} = \sum_{n=0}^{\infty} (-1)^n x^{2n}$ ， $x \in (-1,1)$ 

8.  $\displaystyle \arctan x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{2n+1}$ ， $x \in [-1,1]$ 

    > 利用导数关系  $\displaystyle (\arctan x)'=\frac{1}{1+x^2}$ ，对  $\displaystyle \frac{1}{1+x^2}$  的幂级数在区间  $[0,x]$  上逐项积分： $\displaystyle \int_{0}^{x}\frac{1}{1+t^2}\mathrm{d}t=\int_{0}^{x}\sum\limits_{n=0}^{\infty}(-1)^n t^{2n}\mathrm{d}t$ ，逐项积分后整理得到展开式，积分后端点收敛域扩展至  $x=\pm1$ 。

9.  $\displaystyle \cos x = \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{(2n)!}$ ， $x \in (-\infty,+\infty)$ 

    > 利用导数关系  $(\sin x)'=\cos x$ ，对  $\sin x$  的幂级数展开式逐项求导，对奇数项幂次逐项求导后得到余弦函数展开式，收敛区间保持不变。

10. $\displaystyle (1+x)^\alpha = 1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\dots$ ， $x \in (-1,1)$ （二项式展开）

## 4.3 函数展开为幂级数的两种方法

### （1）直接展开法

步骤：
1. 求函数各阶导数在  $x_0$  处的值；
2. 写出泰勒/麦克劳林级数；
3. 求收敛域；
4. 验证余项极限为0。

### （2）间接展开法（核心常用）

利用已知的基础函数展开式，通过**四则运算、变量代换、逐项求导、逐项积分**变形得到目标函数的幂级数展开式，无需验证余项，计算简便，考试主流方法。
