### 一、lambda 表达式的核心概念
lambda 表达式本质是**匿名的函数对象**（也叫闭包），可以在函数内部定义，直接捕获当前作用域的变量，无需像普通函数那样单独声明/定义，特别适合短逻辑、一次性使用的场景（比如算法库 `std::sort`、`std::for_each` 的参数）。

#### 1. 基本语法
lambda 表达式的完整语法结构如下（方括号 `[]` 和花括号 `{}` 是必须的，其余部分可选）：
```cpp
[capture](parameters) mutable noexcept -> return_type {
    // 函数体（执行逻辑）
}
```
各部分含义：
| 组成部分       | 作用                                                                 |
|----------------|----------------------------------------------------------------------|
| `[capture]`    | 捕获子句：指定从外部作用域捕获哪些变量，以及捕获方式（值/引用）       |
| `(parameters)` | 参数列表：和普通函数的参数列表一致，无参数时可省略（连 `()` 也能省） |
| `mutable`      | 可选：允许修改按值捕获的变量（默认按值捕获的变量是 const 的）         |
| `noexcept`     | 可选：声明 lambda 不会抛出异常                                       |
| `-> return_type` | 可选：显式指定返回值类型，编译器通常能自动推导，简单逻辑可省略     |
| `{}`           | 函数体：lambda 要执行的代码逻辑                                       |

### 二、核心用法详解
#### 1. 最简单的 lambda（无捕获、无参数、无返回值）
这是最基础的形式，直接定义匿名函数并调用：
```cpp
#include <iostream>
using namespace std;

int main() {
    // 定义并立即调用 lambda
    []() {
        cout << "Hello, Lambda!" << endl;
    }();  // 最后的 () 是调用 lambda

    // 省略参数列表（无参数时）
    [] {
        cout << "Lambda without ()" << endl;
    }();

    return 0;
}
```
**输出**：
```
Hello, Lambda!
Lambda without ()
```

#### 2. 带参数的 lambda
和普通函数一样，可接收参数，编译器会自动推导参数类型（也可显式指定）：
```cpp
#include <iostream>
using namespace std;

int main() {
    // 计算两数之和的 lambda
    auto add = [](int a, int b) {
        return a + b;  // 编译器自动推导返回值为 int
    };

    cout << add(3, 5) << endl;  // 输出 8

    // 显式指定返回值（复杂逻辑建议显式指定）
    auto divide = [](double a, double b) -> double {
        if (b == 0) return 0;
        return a / b;
    };
    cout << divide(10, 2) << endl;  // 输出 5

    return 0;
}
```

#### 3. 捕获子句（核心：捕获外部变量）
这是 lambda 最关键的特性，能捕获当前作用域的变量，捕获方式分两种：**值捕获** 和 **引用捕获**。

| 捕获方式       | 语法       | 含义                                                                 |
|----------------|------------|----------------------------------------------------------------------|
| 空捕获         | `[]`       | 不捕获任何外部变量                                                   |
| 值捕获         | `[x, y]`   | 按值捕获变量 x、y（lambda 内是副本，默认不可修改，加 mutable 可修改） |
| 引用捕获       | `[&x, &y]` | 按引用捕获变量 x、y（lambda 内操作的是原变量，可修改）               |
| 全部值捕获     | `[=]`      | 按值捕获所有外部变量                                                 |
| 全部引用捕获   | `[&]`      | 按引用捕获所有外部变量                                               |
| 混合捕获       | `[=, &x]`  | 除 x 按引用捕获，其余都按值捕获；或 `[&, x]`（除 x 按值，其余引用）   |

**示例：捕获变量的使用**
```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10, y = 20;

    // 1. 值捕获：捕获 x、y 的副本
    auto lambda1 = [x, y]() {
        // x++;  // 错误：值捕获的变量默认是 const，不可修改
        cout << "x=" << x << ", y=" << y << endl;  // 输出 x=10, y=20
    };
    lambda1();

    // 2. 值捕获 + mutable：允许修改副本（不影响原变量）
    auto lambda2 = [x, y]() mutable {
        x++;
        y++;
        cout << "副本：x=" << x << ", y=" << y << endl;  // 输出 11,21
    };
    lambda2();
    cout << "原变量：x=" << x << ", y=" << y << endl;  // 输出 10,20（原变量未变）

    // 3. 引用捕获：操作原变量
    auto lambda3 = [&x, &y]() {
        x++;
        y++;
        cout << "引用：x=" << x << ", y=" << y << endl;  // 输出 11,21
    };
    lambda3();
    cout << "原变量：x=" << x << ", y=" << y << endl;  // 输出 11,21（原变量已变）

    // 4. 混合捕获：全部值捕获 + x 引用捕获
    auto lambda4 = [=, &x]() {
        x++;        // x 是引用，可修改原变量
        // y++;     // 错误：y 是值捕获，不可修改
        cout << "混合：x=" << x << ", y=" << y << endl;  // 输出 12,21
    };
    lambda4();

    return 0;
}
```

#### 4. lambda 的典型应用场景
lambda 最常用在 STL 算法中，替代繁琐的函数对象或函数指针：
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> nums = {3, 1, 4, 1, 5, 9};

    // 1. 排序：按降序排列（用 lambda 替代自定义比较函数）
    sort(nums.begin(), nums.end(), [](int a, int b) {
        return a > b;
    });
    // 输出排序结果：9 5 4 3 1 1
    for (int num : nums) cout << num << " ";
    cout << endl;

    // 2. 遍历：输出大于 3 的元素
    cout << "大于 3 的元素：";
    for_each(nums.begin(), nums.end(), [](int num) {
        if (num > 3) cout << num << " ";
    });
    cout << endl;

    return 0;
}
```
**输出**：
```
9 5 4 3 1 1 
大于 3 的元素：9 5 4 
```

### 三、lambda 的进阶特性
1. **lambda 可以赋值给函数对象**：lambda 本质是函数对象，可赋值给 `std::function`（需包含 `<functional>` 头文件）：
   ```cpp
   #include <functional>
   // 定义函数对象类型：接收两个 int，返回 int
   function<int(int, int)> func = [](int a, int b) { return a * b; };
   cout << func(4, 5) << endl;  // 输出 20
   ```

2. **lambda 可以作为返回值**：函数可返回 lambda（需用 `std::function` 包装）：
   ```cpp
   function<int(int)> getLambda() {
       int base = 10;
       return [base](int x) { return x + base; };  // 捕获 base 的副本
   }
   auto f = getLambda();
   cout << f(5) << endl;  // 输出 15
   ```

3. **C++14 泛型 lambda**：参数可使用 `auto`，支持任意类型（类似模板函数）：
   ```cpp
   auto print = [](auto x) {  // C++14 及以上支持
       cout << x << endl;
   };
   print(10);    // 输出 10
   print("abc"); // 输出 abc
   ```

### 总结
1. lambda 是 C++11 引入的**匿名函数对象**，核心优势是「就地定义、捕获外部变量、简洁灵活」，适合短逻辑、一次性使用的场景。
2. 核心语法：`[捕获子句](参数) mutable -> 返回值 { 函数体 }`，其中**捕获子句**是关键（值捕获/引用捕获/混合捕获）。
3. 典型应用：STL 算法（`sort`/`for_each` 等）、回调函数、局部短逻辑，替代繁琐的函数对象/函数指针。