# C++ 操作符重载 复习笔记
## 一、操作符重载基础

### 重载的核心基本原则
1. **只能重载已有运算符**：不可以自定义新的运算符
2. **禁止重载的运算符（共5个）**：
  `.`（成员访问符）、`.*`（成员指针访问符）、`?:`（三目条件运算符）、`::`（作用域解析符）、`sizeof`（大小运算符）
1. **不改变运算符固有属性**：
   - 运算符的优先级、结合性保持不变
   - 操作数个数不变（双目运算符仍为2个操作数，单目运算符仍为1个）
2. **语义建议**：尽量遵循运算符原本的语义

### 两种重载形式对比
| 重载形式 | 本质 | 左操作数来源 | 访问私有成员 |
|---------|------|-------------|-------------|
| 成员函数重载 | 类的成员函数 | 由`this`指针指向当前对象 | 直接访问 |
| 全局（友元）函数重载 | 全局函数 | 全部操作数都通过参数传入 | 需在类内声明为`friend`友元 |

## 二、成员函数形式重载操作符
### 1. 双目操作符重载
#### 语法格式
- 类内声明：
```cpp
class 类名 {
    返回值类型 operator#(参数类型 参数名); // #代表目标运算符，如+、==
};
```
- 类外定义：
```cpp
返回值类型 类名::operator#(参数类型 参数名) {
    // 运算逻辑：左操作数为 this 指向的当前对象，右操作数为参数
}
```
#### 调用等价关系
`a # b` 完全等价于 `a.operator#(b)`，**左操作数必须是本类的对象**。

#### 示例1：复数加法、相等/不等判断
```cpp
class Complex {
    double real, imag;
public:
    Complex(double r=0, double i=0): real(r), imag(i) {}
    Complex operator+(const Complex& x) const {
        Complex temp;
        temp.real = real + x.real;
        temp.imag = imag + x.imag;
        return temp;
    }
    bool operator==(const Complex& x) const {
        return (real == x.real) && (imag == x.imag);
    }
    // 复用 == 的实现，减少代码冗余
    bool operator!=(const Complex& x) const {
        return !(*this == x);
    }
};
Complex a(1,2), b(3,4);
Complex c = a + b; // 等价于 a.operator+(b)
```


### 2. 单目操作符重载
#### 语法格式
- 类内声明：
```cpp
class 类名 {
    返回值类型 operator#(); // 无参数，操作数为当前对象本身
};
```
#### 调用等价关系
`#a` 完全等价于 `a.operator#()`

#### 示例：复数取负
```cpp
class Complex {
    double real, imag;
public:
    Complex operator-() const {
        Complex temp;
        temp.real = -real;
        temp.imag = -imag;
        return temp;
    }
};
Complex a(1,2);
Complex b = -a; // 等价于 a.operator-()
```

## 三、全局（友元）函数形式重载操作符
### 核心规则
- 全局函数重载运算符时，❗**至少有一个参数是类/结构体/枚举类型（或其引用）**，不允许全部参数都是内置类型。
- 若函数需要访问类的私有成员，必须在类内将其声明为`friend`友元函数。

### 1. 双目操作符重载
#### 调用等价关系
`a # b` 完全等价于 `operator#(a, b)`

#### 示例：复数加法（友元版本）
```cpp
class Complex {
    double real, imag;
    friend Complex operator+(const Complex& c1, const Complex& c2);
};

Complex operator+(const Complex& c1, const Complex& c2) {
    return Complex(c1.real + c2.real, c1.imag + c2.imag);
}
```

### 2. 典型应用：混合类型运算
当左操作数不是本类对象时（如`double + Complex`），**无法使用成员函数重载**（成员函数要求左操作数是本类对象，才能调用成员函数），必须使用全局友元函数。

#### 示例：复数与实数的混合加法
```cpp
class Complex {
    double real, imag;
public:
    Complex(double r=0, double i=0): real(r), imag(i) {}
    // 三个重载版本，覆盖所有运算组合
    friend Complex operator+(const Complex& c1, const Complex& c2);
    friend Complex operator+(const Complex& c, double d);
    friend Complex operator+(double d, const Complex& c); // 左操作数是double，必须用友元
};
Complex operator+(const Complex& c1, const Complex& c2) {
    return Complex(c1.real+c2.real, c1.imag+c2.imag);
}
Complex operator+(const Complex& c, double d) {
    return Complex(c.real + d, c.imag);
}
Complex operator+(double d, const Complex& c) {
    return Complex(d + c.real, c.imag);
}
Complex a(1,2);
Complex c2 = a + 21.5;   // 调用 Complex + double 版本
Complex c3 = 10.2 + a;   // 调用 double + Complex 版本
```

### 3. 单目操作符的全局重载
- 普通单目运算符：`返回值类型 operator#(类型 参数)`
- 后置自增/自减：`返回值类型 operator#(类型 参数, int)`，其中`int`是占位参数，仅用于区分前置和后置版本，调用时无需传参。

## 四、特殊操作符的重载⭐
### 1. 自增/自减运算符（++ / --）
#### 前置与后置的区分规则
C++ 通过**占位`int`参数**区分前置和后置重载：
- 前置版本：无额外参数，返回对象引用，支持链式操作
- 后置版本：带一个`int`形参（仅作区分，无实际意义），返回自增/自减前的对象副本

#### 成员函数实现示例
```cpp
class Counter {
    int value;
public:
    Counter(): value(0) {}
    
    // 前置++：返回自身引用
    Counter& operator++() {
        value++;
        return *this;
    }
    
    // 后置++：返回自增前的副本
    const Counter operator++(int) {
        Counter temp = *this; // 保存旧值
        ++(*this);            // 复用前置++的逻辑
        return temp;          // 返回旧值
    }
};

// 使用方式
Counter a;
Counter b = ++a; // 调用前置版本：a先自增，b等于自增后的a
Counter c = a++; // 调用后置版本：c等于自增前的a，a再完成自增
```

> 注意：后置版本返回const临时对象，不能作为左值；工程中通常让后置版本复用前置版本的逻辑，减少代码冗余。

### 2. 赋值运算符（=）
#### 默认行为与问题
编译器会为每个类自动生成默认赋值运算符，执行**逐成员浅拷贝**：
- 普通成员变量：直接赋值
- 类对象成员：递归调用该对象的赋值运算符

当类包含**动态分配的指针成员**时，默认浅拷贝会导致两个严重问题：
1. 内存泄漏：赋值后原对象的堆指针被覆盖，指向的内存无法释放
2. 重复释放：多个对象指向同一块堆内存，析构时会重复释放，导致程序崩溃

#### 自定义赋值运算符（深拷贝标准写法）
```cpp
class A {
    char* p;
    int x, y;
public:
    // 赋值运算符重载：返回自身引用，参数为const引用
    A& operator=(const A& b) {
        // 1. 防止自赋值
        if (&b == this) return *this;
        // 2. 释放自身原有堆资源
        delete[] p;
        // 3. 分配新资源 + 拷贝内容
        p = new char[strlen(b.p) + 1];
        strcpy(p, b.p);
        // 4. 拷贝其他普通成员
        x = b.x;
        y = b.y;
        // 5. 返回自身引用，支持链式赋值
        return *this;
    }
};
```

#### 核心规则与补充
- 赋值运算符**只能作为非静态成员函数重载**，不允许全局函数重载
- 拷贝构造 vs 赋值运算符的本质区别：
  ```cpp
  A a;
  A b = a;  // 拷贝构造：对象创建时的初始化操作
  b = a;    // 赋值运算符：对象已存在，重新赋值
  ```
- 经验法则：需要自定义拷贝构造函数的类，通常也需要自定义赋值运算符。
- 若类包含其他类的对象成员，自定义赋值运算符时**不会自动调用成员对象的赋值运算符**，必须显式编写：
  ```cpp
  class B {
      A a; // 类对象成员
      int x, y;
  public:
      B& operator=(const B& b) {
          a = b.a; // 显式调用A类的赋值运算符
          x = b.x;
          y = b.y;
          return *this;
      }
  };
  ```

### 3. 下标访问运算符（[]）
#### 用途
让类对象可以像数组一样通过下标访问元素，常用于字符串类、自定义数组类，同时可以实现下标越界检查。

#### 语法与示例
```cpp
class String {
    char* p;
public:
    // 返回引用，支持下标表达式作为左值修改元素
    char& operator[](int i) {
        // 下标越界检查
        if (i < 0 || i >= strlen(p)) {
            cerr << "下标越界错误\n";
            exit(-1);
        }
        return p[i];
    }
};

// 使用方式
String s("abcdefg");
s[0] = 'x'; // 合法，因为运算符返回引用
```

> 注意：只能作为成员函数重载；返回引用是为了支持下标表达式作为左值。

### 4. 函数调用运算符（()）
#### 用途
重载后类的对象可以像函数一样调用，也称为**仿函数（functor）**，常用于STL算法的自定义策略。

#### 语法与示例
```cpp
class AddValue {
    int base;
public:
    AddValue(int i): base(i) {}
    
    // 重载()，参数和返回值可自定义，支持多版本重载
    int operator()(int x) {
        return x + base;
    }
};

// 使用方式
AddValue add3(3);
cout << add3(10); // 等价于 add3.operator()(10)，输出13
```

> 注意：只能作为非静态成员函数实现；支持多个参数，支持函数重载。

### 5. 成员访问运算符（->）
#### 用途
实现**智能指针**，在访问目标对象成员时可以附加额外逻辑（

#### 规则
- 只能作为非静态成员函数重载
- 按单目运算符形式实现，返回指向目标类的指针


### 6. 自定义类型转换
C++ 支持两种方向的自定义类型转换，分别由转换构造函数和类型转换运算符实现。

#### （1）其他类型 → 本类类型：转换构造函数
带单个参数的构造函数可以作为类型转换函数，将参数类型隐式转换为本类对象。
```cpp
class Complex {
    double real, imag;
public:
    // 单参数构造函数：支持 double → Complex 的隐式转换
    Complex(double r): real(r), imag(0) {}
};

Complex c1(1,2);
Complex c2 = c1 + 1.7; // 1.7 隐式转换为 Complex(1.7)
```

#### （2）本类类型 → 其他类型：类型转换运算符
```cpp
class Point {
    int x, y;
public:
    // 类型转换运算符：无返回值类型，函数名就是目标类型，无参数
    operator int() {
        return x + y;
    }
};

Point p;
int z = 1 + p; // p 隐式转换为 int 类型
```

#### 二义性问题与解决方案
如果类同时存在**转换构造函数**和**类型转换运算符**，运算时可能出现二义性：
```cpp
// 同时存在 A(int) 构造函数 和 operator int()
z = a + i; // 歧义：a转int？还是i转A？
```
两种解决方案：
1. 显式类型转换：`z = (int)a + i;` 或 `z = a + (A)i;`
2. 用`explicit`修饰构造函数，禁止隐式转换：
   ```cpp
   explicit A(int i) { ... } // 仅允许显式转换，禁止隐式转换
   ```

## 五、核心总结与易混点
### 1. 只能作为成员函数重载的运算符
共4个：`=`、`[]`、`()`、`->`

### 2. 成员函数 vs 友元函数的选择
- 左操作数必须是本类对象 → 优先使用成员函数
- 左操作数需要支持内置类型/其他类 → 必须使用全局友元函数
- 单目运算符优先成员函数实现，双目运算符可按需选择

### 3. 返回值设计原则
- 赋值类运算符（=、+=等）、前置自增自减 → 返回自身引用，支持链式操作
- 算术运算（+、-等） → 返回值对象（临时对象）
- 后置自增自减 → 返回const临时对象，避免`a++++`这类不合理写法

下面是考试和开发中最常用的运算符的固定写法，可以直接对照使用：

| 运算符 | 成员函数声明（标准写法） | 全局友元声明（标准写法） |
|-------|------------------------|------------------------|
| 加法 `+` | `A operator+(const A& a) const;` | `friend A operator+(const A& a, const A& b);` |
| 相等 `==` | `bool operator==(const A& a) const;` | `friend bool operator==(const A& a, const A& b);` |
| 赋值 `=` | `A& operator=(const A& a);` | 不允许重载 |
| 下标 `[]` | `char& operator[](int index);` | 不允许重载 |
| 函数调用 `()` | `int operator()(int x);` | 不允许重载 |
| 成员访问 `->` | `T* operator->();` | 不允许重载 |
| 前置⭐ `++` | `A& operator++();` | `friend A& operator++(A& a);` |
| 后置⭐ `++` | `const A operator++(int);` | `friend const A operator++(A& a, int);` |
| 单目取负 `-` | `A operator-() const;` | `friend A operator-(const A& a);` |
| 流插入⭐ `<<` | 不建议重载（左操作数须为`ostream`对象） | `friend ostream& operator<<(ostream& out, const A& c);` |
| 流提取⭐ `>>` | 不建议重载（左操作数须为`istream`对象） | `friend istream& operator>>(istream& is, A& c);` |
