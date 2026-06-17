## 导数与微分
### 导数
**定义**
$$f'(x_0) = \lim_{\Delta x \to 0} \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}$$
$$=\lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h}= \lim_{x \to x_0} \frac{f(x) - f(x_0)}{x - x_0} $$
- 可导 $\Rightarrow$ 连续
- 可导 $\Leftrightarrow\lim\limits_{x\to x_0}\dfrac{\Delta y}{\Delta x}$ 存在 $\Leftrightarrow f'_-(x_0)=f'_+(x_0)$
  
**法则**
- $$(uvw)'= u'vw + uv'w + uvw'$$
- **反函数的导数等于原函数导数的倒数**:设函数 \( y = f(x) \) 在区间 \( I \) 内**单调、可导**，且 \( f'(x) \neq 0 \)，则其反函数 \( x = f^{-1}(y) \) 在对应的区间 \( J = \{y \mid y = f(x), x \in I\} \) 内也可导，且
\[
\left[f^{-1}(y)\right]' = \frac{1}{f'(x)}
\quad或\quad
\frac{\mathrm dx}{\mathrm dy} = \frac{1}{\dfrac{\mathrm dy}{\mathrm dx}}
\]
- $$\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm du}\cdot\frac{\mathrm du}{\mathrm dv}\cdot\frac{\mathrm dv}{\mathrm dx}$$

**公式**
\[
\begin{align*}
(\tan x)' = \sec^2 x = \frac{1}{\cos^2 x}\quad\quad
(\sec x)' = \sec x \cdot \tan x \\
(\cot x)' = -\csc^2 x = -\frac{1}{\sin^2 x} \quad 
(\csc x)' = -\csc x \cdot \cot x
\end{align*}
\]
\[
\begin{align*}
(\arcsin x)' &= \frac{1}{\sqrt{1-x^2}} \quad (x\in(-1,1)) \\
(\arccos x)' &= -\frac{1}{\sqrt{1-x^2}} \quad (x\in(-1,1)) \\
(\arctan x)' &= \frac{1}{1+x^2} \\
(\text{arccot }x)' &= -\frac{1}{1+x^2}
\end{align*}
\]
### 高阶导数
表示：
$$y^{(n)}\quad或\quad\frac{\mathrm d^ny}{\mathrm dx^n}$$
**高阶导数公式**：
\[
\begin{gather*}
(x^n)^{(n)} = n!\\
\left(\frac{1}{x}\right)^{(n)} = \frac{(-1)^n n!}{x^{n+1}}\\
(e^x)^{(n)} = e^x\\
(\sin x)^{(n)} = \sin\left(x + n \cdot \frac{\pi}{2}\right)\\
(\cos x)^{(n)} = \cos\left(x + n \cdot \frac{\pi}{2}\right)\\
[\ln(1+x)]^{(n)} = (-1)^{n-1} \frac{(n-1)!}{(1+x)^n}\ (x > -1)
\end{gather*}
\]

**线性运算公式**：
\[(\alpha u + \beta v)^{(n)} = \alpha u^{(n)} + \beta v^{(n)}（其中\alpha, \beta \in \mathbb{R}）\]
**莱布尼茨公式**：
\[(uv)^{(n)} = \sum_{k=0}^{n} \mathrm{C}_{n}^{k} u^{(n-k)} v^{(k)}\]
### 隐函数求导
方程两边同时对自变量求导
### 对数求导法
- 针对$f(x)^{g(x)}$型和$\sqrt{\dfrac{f(x)g(x)}{h(x)p(x)}}$型：
- 方程两边同取对数，再求导
### 参数方程求导
1. **一阶导数**：
\[
\frac{\mathrm dy}{\mathrm dx} = \frac{\mathrm dy}{\mathrm dt} \cdot \frac{\mathrm dt}{\mathrm dx} = \frac{\frac{\mathrm dy}{\mathrm dt}}{\frac{\mathrm dx}{\mathrm dt}} = \frac{\psi'(t)}{\varphi'(t)}
\]

1. **二阶导数**：
\[
\frac{\mathrm d^2 y}{\mathrm dx^2} = \frac{\mathrm d}{\mathrm dx}\left( \frac{\mathrm dy}{\mathrm dx} \right) = \frac{\mathrm d}{\mathrm dt}\left( \frac{\psi'(t)}{\varphi'(t)} \right)\frac{\mathrm dt}{\mathrm dx} = \frac{\psi''(t)\varphi'(t) - \psi'(t)\varphi''(t)}{\left[ \varphi'(t) \right]^3}
\]
### 微分
函数\( f(x) \)在点\( x_0 \)处可导，且微分表达式为 $df(x) = f'(x_0) \Delta x$
- 可导 $\Leftrightarrow$ 可微
- 微分形式不变性
\(\mathrm dy = f'(u) \cdot g'(x) \mathrm dx \)，\( \mathrm du = g'(x) \mathrm dx\Rightarrow \) \(\mathrm dy = f'(u) \mathrm du \)

## 微分中值定理与导数的应用
### 微分中值定理
- **费马引理**：设函数$f(x)$在点$x_0$的某邻域$U(x_0)$内有定义，并且在$x_0$处可导，如果对任意的$x \in U(x_0)$，有$f(x) \leq f(x_0)（或f(x) \geq f(x_0)），$那么$f'(x_0)=0$

#### 罗尔定理
如果函数$f(x)$满足
1. 在闭区间$[a,b]$上连续；
2. 在开区间$(a,b)$内可导；
3. 在区间端点处的函数值相等，即$f(a)=f(b),$

那么在$(a,b)$内至少存在一点$\xi$，使得$f'(\xi)=0．$
#### 拉格朗日中值定理
如果函数$f(x)$满足
1. 在闭区间$[a,b]$上连续；
2. 在开区间$(a,b)$内可导，

那么在$(a,b)$内至少存在一点$\xi$，使得$f(b)-f(a)=f'(\xi)(b-a).$
- **有限增量形式**：$\Delta y = f'(x+\theta\Delta x)\cdot\Delta x\ (0<\theta<1).$
- **定理**：如果函数$f(x)$在区间$I$上的导数恒为零，那么$f(x)$在区间$I$上是一个常数
#### 柯西中值定理
如果函数$f(x)$及$F(x)$满足
1. 在闭区间$[a,b]$上连续；
2. 在开区间$(a,b)$内可导；
3. 对任一$x \in (a,b)$，$F'(x) \neq 0$，

那么在$(a,b)$内至少存在一点$\xi$，使得
$$\frac{f(b)-f(a)}{F(b)-F(a)} = \frac{f'(\xi)}{F'(\xi)}.$$
### 洛必达法则
$$\lim\limits_{x \to a} \frac{f(x)}{F(x)} = \lim\limits_{x \to a} \frac{f'(x)}{F'(x)}.$$
条件：
   1. $\lim\limits_{\substack{x \to a \\(x \to \infty)}} f(x) = \lim\limits_{\substack{x \to a\\ (x \to \infty)}} F(x) = 0/\infin$；
   2. 在点$a$的某去心邻域内，$f'(x)$及$F'(x)$都存在，且$F'(x) \neq 0$；(当$|x|>N$时$f'(x)$与$g'(x)$都存在，且$F'(x)\neq0$)
   3. $\lim\limits_{\substack{x \to a\\(x \to \infty)}} \dfrac{f'(x)}{F'(x)}$存在(或为无穷大)，


### 泰勒公式
若函数 \( f(x) \) 在点 \( x_0 \) 的某邻域内具有 \( n+1 \) 阶导数，则对该邻域内任意一点 \( x \)，有：
\(
f(x) = f(x_0) + f'(x_0)(x-x_0) + \dfrac{f''(x_0)}{2!}(x-x_0)^2 + \dots + \dfrac{f^{(n)}(x_0)}{n!}(x-x_0)^n + R_n(x)
\)
其中 \( R_n(x) \) 称为**余项**，常见有两种形式：

1.  **皮亚诺余项**
    \[
    R_n(x) = o\left((x-x_0)^n\right)
    \]
    这种形式的泰勒公式不要求 \( f(x) \) 存在 \( n+1 \) 阶导数，仅需 \( n \) 阶导数在 \( x_0 \) 处存在即可。

2.  **拉格朗日余项**
    \[
    R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}
    \]
    其中 \( \xi \) 介于 \( x_0 \) 与 \( x \) 之间。

### 麦克劳林公式
当 \( x_0=0 \) 时，泰勒公式就退化为**麦克劳林公式**：
\[
f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \dots + \frac{f^{(n)}(0)}{n!}x^n + R_n(x)
\]
对应的皮亚诺余项为 \( R_n(x)=o(x^n) \)，拉格朗日余项为 \( R_n(x)=\dfrac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1} \ (0<\theta<1) \)。
### 常用麦克劳林公式（带皮亚诺余项）⭐
当 \( x \to 0 \) 时，
1. \( \mathrm{e}^x = 1 + x + \dfrac{x^2}{2!} + \dfrac{x^3}{3!} + \dots + \dfrac{x^n}{n!} + o(x^n) \)
2. \( \sin x = x - \dfrac{x^3}{3!} + \dfrac{x^5}{5!} - \dots + (-1)^{k-1}\dfrac{x^{2k-1}}{(2k-1)!} + o(x^{2k}) \)
3. \( \cos x = 1 - \dfrac{x^2}{2!} + \dfrac{x^4}{4!} - \dots + (-1)^k\dfrac{x^{2k}}{(2k)!} + o(x^{2k+1}) \)
4. \( \ln(1+x) = x - \dfrac{x^2}{2} + \dfrac{x^3}{3} - \dots + (-1)^{n-1}\dfrac{x^n}{n} + o(x^n) \)
5. \( (1+x)^\alpha = 1 + \alpha x + \dfrac{\alpha(\alpha-1)}{2!}x^2 + \dots + \dfrac{\alpha(\alpha-1)\dots(\alpha-n+1)}{n!}x^n + o(x^n) \)（\( \alpha \in \mathbb{R} \)）
### 凹凸性
- 设 \( f(x) \) 在区间 \( I \) 上连续，对 \( I \) 上任意两点 \( x_1, x_2 \)：
1. 若恒有 \( f\left( \frac{x_1 + x_2}{2} \right) < \frac{f(x_1) + f(x_2)}{2} \)，则称 \( f(x) \) 在 \( I \) 上的图形是***(向上)凹的（或凹弧）****；
2. 若恒有 \( f\left( \frac{x_1 + x_2}{2} \right) > \frac{f(x_1) + f(x_2)}{2} \)，则称 \( f(x) \) 在 \( I \) 上的图形是**(向上)凸的（或凸弧）**
- 设 \( f(x) \) 在 \([a, b]\) 上连续，在 \((a, b)\) 内具有一阶和二阶导数，那么
1. 若在 \((a, b)\) 内 \( f''(x) > 0 \)，则 \( f(x) \) 在 \([a, b]\) 上的图形是凹的；
2. 若在 \((a, b)\) 内 \( f''(x) < 0 \)，则 \( f(x) \) 在 \([a, b]\) 上的图形是凸的。
### 极值
#### 定义 
设函数\( f(x) \)在点\( x_0 \)的某邻域\( U(x_0) \)内有定义，如果对该邻域内的任一\( x \ (x \neq x_0) \)，有
\[ f(x) < f(x_0) \ (\text{或} \ f(x) > f(x_0)) \]
那么就称\( f(x_0) \)是函数\( f(x) \)的一个**极大值**(或**极小值**)。

- 函数的极大值与极小值统称为**极值**，使函数取得极值的点称为**极值点**。

#### 必要条件
 设函数\( f(x) \)在\( x_0 \)处可导，且在\( x_0 \)处取得极值，那么\( f'(x_0) = 0 \)

- 可导函数的极值点一定是驻点，但驻点不一定是极值点。

#### 第一充分条件
设函数\( f(x) \)在\( x_0 \)连续，且在\( x_0 \)的某去心邻域内可导：
1. 若\( x < x_0 \)时，\( f'(x) > 0 \)，而\( x > x_0 \)时，\( f'(x) < 0 \)（左正右负），则\( f(x) \)在\( x_0 \)处取得极大值；
2. 若\( x < x_0 \)时，\( f'(x) < 0 \)，而\( x > x_0 \)时，\( f'(x) > 0 \)（左负右正），则\( f(x) \)在\( x_0 \)处取得极小值；
3. 若在\( x_0 \)的左右两侧\( f'(x) \)不变号，则\( f(x) \)在\( x_0 \)处不取得极值。

#### 第二充分条件
设函数\( f(x) \)在\( x_0 \)处具有二阶导数，且\( f'(x_0) = 0 \)、\( f''(x_0) \neq 0 \)，那么：
1. 当\( f''(x_0) < 0 \)时，函数\( f(x) \)在\( x_0 \)处取得极大值；
2. 当\( f''(x_0) > 0 \)时，函数\( f(x) \)在\( x_0 \)处取得极小值。
### 渐近线
#### 1. 垂直渐近线
- **定义**：若 \( \lim\limits_{x \to x_0^+} f(x) = \infty \) 或 \( \lim\limits_{x \to x_0^-} f(x) = \infty \)，则直线 \( x = x_0 \) 是 \( f(x) \) 的垂直渐近线。
- **核心**：函数在 \( x_0 \) 处无定义（或极限为无穷），通常出现在分母为0的点。
- **示例**：\( f(x) = \frac{1}{x} \)，当 \( x \to 0 \) 时 \( f(x) \to \infty \)，故 \( x = 0 \) 是垂直渐近线。


#### 2. 水平渐近线
- **定义**：若 \( \lim\limits_{x \to +\infty} f(x) = A \) 或 \( \lim\limits_{x \to -\infty} f(x) = A \)（\( A \) 为常数），则直线 \( y = A \) 是 \( f(x) \) 的水平渐近线。
- **核心**：函数在无穷远处趋近于某常数，同一函数最多有2条水平渐近线（正负无穷方向各一条）。
- **示例**：\( f(x) = \frac{1}{x} \)，当 \( x \to \pm\infty \) 时 \( f(x) \to 0 \)，故 \( y = 0 \) 是水平渐近线。


#### 3. 斜渐近线
- **定义**：若 \( \lim\limits_{x \to \pm\infty} \dfrac{f(x)}{x} = a \)（\( a \neq 0 \)，常数），且 \( \lim\limits_{x \to \pm\infty} [f(x) - ax] = b \)（\( b \) 为常数），则直线 \( y = ax + b \) 是 \( f(x) \) 的斜渐近线。
- **核心**：函数在无穷远处的趋势与一次函数一致，同一函数最多有2条斜渐近线（正负无穷方向各一条）。
- **示例**：\( f(x) = \dfrac{x^2 + 1}{x} = x + \dfrac{1}{x} \)，当 \( x \to \pm\infty \) 时，\( \dfrac{f(x)}{x} \to 1 \)，\( f(x) - x \to 0 \)，故 \( y = x \) 是斜渐近线。

#### 注意
- 同一函数在同一无穷方向上，**水平渐近线与斜渐近线不会同时存在**（若水平渐近线存在，则 \( \lim\limits_{x \to \infty} \dfrac{f(x)}{x} = 0 \)，不满足斜渐近线的 \( a \neq 0 \)）。
- 垂直渐近线是“垂直直线”，水平/斜渐近线是“水平/倾斜直线”。

