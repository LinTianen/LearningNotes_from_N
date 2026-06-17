# C语言文件输入输出（I/O）函数详解

### 速查

一、文件打开与关闭函数
`FILE *fopen(文件名, 使用文件方式)`
`int fclose(fp)`
二、字符级读写函数
`int fgetc(fp)`
`int fputc(ch, fp)`
三、行级读写函数
`char *fgets(str, n, fp)`
`int fputs(str, fp)`
四、格式化读写函数
`int fscanf(fp, 格式字符串, 输入表列)`
`int fprintf(fp, 格式字符串, 输入表列)`
五、块级（二进制）读写函数
`size_t fread(buffer, size, count, fp)`
`size_t fwrite(buffer, size, count, fp)`
`buffer`:地址，`size`:要读写的字节数 `count`:要读取多少个数据项
六、文件定位函数
`int fseek(fp, 位移量, 起始点)`
`long ftell(fp)`
`void rewind(fp)`

## 一、文件操作的基础概念

在C语言中，文件操作依赖标准库`<stdio.h>`，核心是**文件指针（** **`FILE*`** **）**——它是一个指向文件信息结构体的指针，用于关联具体文件，后续所有文件操作都通过该指针完成。

文件打开模式分为文本模式和二进制模式，核心区别：

- 文本模式：处理文本文件，会自动转换换行符（Windows下`\r\n`与`\n`互转），模式标识不带`b`。

- 二进制模式：处理非文本文件（图片、音频等），不做任何字符转换，模式标识带`b`（如`rb`、`wb`）。

## 二、核心文件操作函数

### 1. 文件打开函数：`fopen()`

用于打开指定文件，返回文件指针（打开失败返回`NULL`，需校验返回值）。

#### 函数原型

```C
FILE *fopen(const char *filename, const char *mode);
```

#### 参数说明

- `filename`：文件路径（相对路径或绝对路径，字符串类型）。

- `mode`：打开模式，常用取值如下：

|模式|含义（文本模式）|二进制对应|适用场景|
|---|---|---|---|
|`r`|只读，文件必须存在|`rb`|读取已有文本文件|
|`w`|只写，文件不存在则创建，存在则清空内容|`wb`|新建/覆盖文本文件|
|`a`|追加，文件不存在则创建，写入内容追加到文件末尾|`ab`|向文本文件末尾添加内容|
|`r+`|读写，文件必须存在|`rb+`|读取并修改已有文件|
|`w+`|读写，文件不存在则创建，存在则清空|`wb+`|新建文件并同时读写|
|`a+`|读写，文件不存在则创建，写入仅追加|`ab+`|读取文件并向末尾追加内容|

#### 示例（打开文件）

```C
#include <stdio.h>
#include <stdlib.h> // 用于exit()

int main() {
    // 以只读模式打开文本文件，若失败则提示并退出
    FILE *fp = fopen("test.txt", "r");
    if (fp == NULL) {
        perror("fopen failed"); // 打印错误信息
        exit(EXIT_FAILURE);
    }
    // 后续操作...
    return 0;
}
```

### 2. 文件关闭函数：`fclose()`

用于关闭已打开的文件，释放文件资源，避免内存泄漏和文件损坏（打开文件后必须关闭）。

#### 函数原型

```C
int fclose(FILE *stream);
```

#### 参数与返回值

- `stream`：已打开的文件指针。

- 返回值：成功返回0，失败返回`EOF`（宏定义，值为-1）。

#### 示例（关闭文件）

```C
// 承接上面的示例
fclose(fp);
fp = NULL; // 避免野指针
```

### 3. 字符级读写函数：`fgetc()` 与 `fputc()`

适用于逐个字符读写文件，精度细，适合处理文本文件的字符遍历。

#### （1）字符读取函数：`fgetc()`

从文件中读取一个字符，读取到文件末尾或失败时返回`EOF`。

##### 函数原型

```C
int fgetc(FILE *stream);
```

#### （2）字符写入函数：`fputc()`

向文件中写入一个字符，成功返回写入的字符，失败返回`EOF`。

##### 函数原型

```C
int fputc(int ch, FILE *stream);
```

#### 示例（字符读写）

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    // 写入字符到文件
    FILE *fp_w = fopen("char.txt", "w");
    if (fp_w == NULL) { perror("fopen write failed"); exit(1); }
    fputc('H', fp_w);
    fputc('e', fp_w);
    fputc('l', fp_w);
    fclose(fp_w);

    // 从文件读取字符
    FILE *fp_r = fopen("char.txt", "r");
    if (fp_r == NULL) { perror("fopen read failed"); exit(1); }
    int ch; // 用int接收，避免EOF（-1）与字符混淆
    while ((ch = fgetc(fp_r)) != EOF) {
        printf("%c", ch); // 输出：Hell
    }
    fclose(fp_r);
    return 0;
}
```

### 4. 行级读写函数：`fgets()` 与 `fputs()`

适用于按行读写文本文件，处理带换行符的字符串更便捷。

#### （1）行读取函数：`fgets()`

从文件读取一行字符串，自动在末尾添加`\0`结束符，读取成功返回字符串指针，失败/文件末尾返回`NULL`。

##### 函数原型

```C
char *fgets(char *str, int n, FILE *stream);
```

- 说明：最多读取`n-1`个字符（留一个存`\0`），遇到`\n`或文件末尾停止读取，`\n`会被包含在字符串中。

#### （2）行写入函数：`fputs()`

向文件写入一行字符串，不会自动添加`\n`，成功返回非负整数，失败返回`EOF`。

##### 函数原型

```C
int fputs(const char *str, FILE *stream);
```

#### 示例（行读写）

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    // 写入行到文件
    FILE *fp_w = fopen("line.txt", "w");
    if (fp_w == NULL) { perror("fopen write failed"); exit(1); }
    fputs("Hello C language\n", fp_w); // 手动添加\n换行
    fputs("File I/O functions", fp_w);
    fclose(fp_w);

    // 从文件读取行
    FILE *fp_r = fopen("line.txt", "r");
    if (fp_r == NULL) { perror("fopen read failed"); exit(1); }
    char buf[1024]; // 缓冲区存储读取的行
    while (fgets(buf, sizeof(buf), fp_r) != NULL) {
        printf("%s", buf); // 输出：Hello C language + 换行 + File I/O functions
    }
    fclose(fp_r);
    return 0;
}
```

### 5. 格式化读写函数：`fscanf()` 与 `fprintf()`

类似`scanf()`和`printf()`，但读写对象是文件而非控制台，支持按格式读写各种数据类型（int、float、字符串等）。

#### （1）格式化读取函数：`fscanf()`

从文件按指定格式读取数据，成功返回读取的变量个数，失败/文件末尾返回`EOF`。

##### 函数原型

```C
int fscanf(FILE *stream, const char *format, ...);
```

#### （2）格式化写入函数：`fprintf()`

向文件按指定格式写入数据，成功返回写入的字符总数，失败返回负数。

##### 函数原型

```C
int fprintf(FILE *stream, const char *format, ...);
```

#### 示例（格式化读写）

```C
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    char name[20];
    int age;
    float score;
} Student;

int main() {
    // 格式化写入结构体数据
    Student stu = {"Zhang San", 18, 95.5};
    FILE *fp_w = fopen("format.txt", "w");
    if (fp_w == NULL) { perror("fopen write failed"); exit(1); }
    fprintf(fp_w, "Name: %s, Age: %d, Score: %.1f", stu.name, stu.age, stu.score);
    fclose(fp_w);

    // 格式化读取数据
    Student stu_read;
    FILE *fp_r = fopen("format.txt", "r");
    if (fp_r == NULL) { perror("fopen read failed"); exit(1); }
    fscanf(fp_r, "Name: %s, Age: %d, Score: %f", stu_read.name, &stu_read.age, &stu_read.score);
    printf("Read data: %s, %d, %.1f\n", stu_read.name, stu_read.age, stu_read.score);
    fclose(fp_r);
    return 0;
}
```

### 6. 块级读写函数：`fread()` 与 `fwrite()`

适用于二进制模式下的批量数据读写（如结构体、数组），按字节块操作，效率高，是处理非文本文件的首选。

#### （1）块写入函数：`fwrite()`

向文件写入指定数量的数据块，成功返回实际写入的块数，失败返回小于指定块数的值。

##### 函数原型

```C
size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream);
```

- 参数说明：

    - `ptr`：待写入数据的内存地址（指针）。

    - `size`：每个数据块的字节大小。

    - `nmemb`：要写入的块数。

    - `stream`：文件指针（需二进制模式打开）。

#### （2）块读取函数：`fread()`

从文件读取指定数量的数据块，成功返回实际读取的块数，失败/文件末尾返回小于指定块数的值。

##### 函数原型

```C
size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream);
```

#### 示例（块级读写，二进制文件）

```C
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    char name[20];
    int age;
    float score;
} Student;

int main() {
    Student stus[2] = {{"Li Si", 19, 92.0}, {"Wang Wu", 20, 88.5}};
    // 二进制模式写入（wb）
    FILE *fp_w = fopen("student.dat", "wb");
    if (fp_w == NULL) { perror("fopen write failed"); exit(1); }
    // 写入2个结构体，每个结构体大小为sizeof(Student)
    size_t write_num = fwrite(stus, sizeof(Student), 2, fp_w);
    printf("Write %zu students\n", write_num); // 输出：Write 2 students
    fclose(fp_w);

    // 二进制模式读取（rb）
    Student stus_read[2];
    FILE *fp_r = fopen("student.dat", "rb");
    if (fp_r == NULL) { perror("fopen read failed"); exit(1); }
    size_t read_num = fread(stus_read, sizeof(Student), 2, fp_r);
    printf("Read %zu students:\n", read_num);
    for (int i = 0; i < read_num; i++) {
        printf("Name: %s, Age: %d, Score: %.1f\n", 
               stus_read[i].name, stus_read[i].age, stus_read[i].score);
    }
    fclose(fp_r);
    return 0;
}
```

### 7. 文件定位函数：`fseek()`、`ftell()`、`rewind()`

用于移动文件指针的位置，实现随机读写（默认文件指针按读写顺序向后移动）。

#### （1）`fseek()`：设置文件指针位置

##### 函数原型

```C
int fseek(FILE *stream, long offset, int whence);
```

- 参数说明：

    - `offset`：偏移量（正数向后移，负数向前移，单位：字节）。

    - `whence`：基准位置，可选3个宏：

        - `SEEK_SET`(0)：文件开头（基准位置为0）。

        - `SEEK_CUR`(1)：文件指针当前位置。

        - `SEEK_END`(2)：文件末尾。

- 返回值：成功返回0，失败返回非0。

#### （2）`ftell()`：获取文件指针当前位置

##### 函数原型

```C
long ftell(FILE *stream);
```

- 返回值：成功返回当前位置相对于文件开头的字节数，失败返回-1L。

#### （3）`rewind()`：将文件指针重置到文件开头

##### 函数原型

```C
void rewind(FILE *stream);
```

#### 示例（文件定位）

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *fp = fopen("seek.txt", "w+");
    if (fp == NULL) { perror("fopen failed"); exit(1); }

    // 写入数据
    fprintf(fp, "0123456789");
    printf("当前指针位置：%ld\n", ftell(fp)); // 输出：10（写入10个字符）

    // 移动指针到文件开头后第3个字节
    fseek(fp, 3, SEEK_SET);
    char ch;
    fscanf(fp, "%c", &ch);
    printf("读取的字符：%c\n", ch); // 输出：3

    // 移动指针到当前位置前2个字节
    fseek(fp, -2, SEEK_CUR);
    fscanf(fp, "%c", &ch);
    printf("读取的字符：%c\n", ch); // 输出：2

    // 重置指针到文件开头
    rewind(fp);
    fscanf(fp, "%c", &ch);
    printf("读取的字符：%c\n", ch); // 输出：0

    fclose(fp);
    return 0;
}
```

## 三、关键注意事项

1. **必须校验** **`fopen()`** **返回值**：文件不存在、权限不足等会导致打开失败，返回`NULL`，不校验会引发野指针错误。

2. **文件使用后必须关闭**：`fclose()`会刷新缓冲区，确保数据写入文件，同时释放系统资源，避免资源泄漏。

3. **文本模式与二进制模式区分**：处理图片、视频等二进制文件时，必须使用`b`模式，否则会导致数据损坏。

4. **`fgetc()`** **用** **`int`** **接收**：`EOF`的值是-1，若用`char`接收，无法区分有效字符（如ASCII码0xFF）和`EOF`。

5. **块级读写适合二进制文件**：`fread()`/`fwrite()`读写文本文件时，会保留原始字节，可能出现换行符混乱问题。

## 总结

C语言文件I/O函数按功能可分为4大类，核心要点如下：

1. **打开/关闭**：`fopen()`（指定模式）+ `fclose()`（释放资源），是文件操作的入口和出口。

2. **数据读写**：

    - 字符级：`fgetc()`/`fputc()`（逐个字符）。

    - 行级：`fgets()`/`fputs()`（按行处理文本）。

    - 格式化：`fscanf()`/`fprintf()`（按格式读写基本类型/结构体）。

    - 块级：`fread()`/`fwrite()`（二进制批量读写，效率最高）。

3. **文件定位**：`fseek()`（设置位置）、`ftell()`（获取位置）、`rewind()`（重置开头），支持随机读写。

4. **模式选择**：文本文件用普通模式（`r`/`w`/`a`），二进制文件用`b`模式（`rb`/`wb`/`ab`）。