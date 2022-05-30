---
layout: post
title:  "C++01.基础修饰符"
date:   2022-05-29
excerpt: "cpp.基础修饰符"
tag:
- C++
- 基础修饰符
- const
- static
comments: false
---

<center><b>01.基础修饰符.</b> </center>

# C++01.基础修饰符

## 一.const修饰符

### 1.作用

- 定义常量

- 类型检查

- 防止修改，起保护作用，增加程序健壮性

- 节省空间，避免不必要的内存分配

  const定义常量从汇编的角度来看，只是给出了对应的内存地址，而不是像`#define`一样给出的是立即数。

  const定义的常量在程序运行过程中只有一份拷贝，而`#define`定义的常量在内存中有若干个拷贝。

### 2.与define对比

1. const常量具有类型，编译器可以进行安全检查；#define宏定义没有数据类型，为简单的字符串替换，不能进行安全检查。
2. const定义的变量只有类型为整数或者枚举，且以常量表达式初始化时才作为常量表达式。

### 3.const对象与extern

非const变量默认为extern。要使const变量能够在其他文件中访问，必须在文件中显式地指定它为extern，且需要做初始化。

### 4.指针与const

```c++
const char * a; //指向const对象的指针或者说指向常量的指针。
char const * a; //同上
char * const a; //指向类型对象的const指针。或者说常指针、const指针。
const char * const a; //指向const对象的const指针。
```

### 5.函数中使用const

- 修饰函数返回值

- 修饰函数参数

  - 参数指针多指内容为常量不可变

    ```c++
    void StringCopy(char *dst, const char *src);
    ```

    其中src 是输入参数，dst 是输出参数。给src加上const修饰后，如果函数体内的语句试图改动src的内容，编译器将指出错误。这就是加了const的作用之一。

  - 参数为引用

    作用：增加效率同时防止修改

    ```c++
    void func(const A &a)
    ```

    对于非内部数据类型的参数而言，像void func(A a) 这样声明的函数注定效率比较低。因为函数体内将产生A 类型的临时对象用于复制参数a，而临时对象的构造、复制、析构过程都将消耗时间。

    为了提高效率，可以将函数声明改为void func(A &a)，因为“引用传递”仅借用一下参数的别名而已，不需要产生临时对象。

    > 但是函数void func(A &a) 存在一个缺点：
    >
    > “引用传递”有可能改变参数a，这是我们不期望的。解决这个问题很容易，加const修饰即可，因此函数最终成为 void func(const A &a)。

    但对于下列内部数据类型的参数：

    ```c++
    void func(int x)
    void func(const int &x)
    ```

    没有必要改写，因为内部数据类型的参数不存在构造，析构的过程，复制非常快，“值传递”与“引用传递”的效率相当。

### 6.类中使用const

- 只有常成员函数才可以操作常量或常对象
- const对象只能访问const成员函数
- 非const对象可以访问任意的成员函数，包括xonst成员函数
- 类中的const成员变量必须通过初始化列表进行初始化



## 二.static修饰符

### 1.静态变量

- 函数中的静态变量

  当变量声明为static时，**空间将在程序的生命周期内分配**。即使多次调用该函数，静态变量的空间也只分配一次，前一次调用中的变量值通过下一次函数调用传递。

- 类中的静态变量

  由于声明为static的变量只被初始化一次，因为它们在单独的静态存储中分配了空间，因此**类中的静态变量由对象共享**。对于不同的对象，不能有相同静态变量的多个副本。也是因为这个原因，**静态变量不能使用构造函数初始化**。

### 2.静态成员

- 类对象为静态

  静态对象的范围是贯穿程序的生命周期。

- 类中的静态函数

  静态成员函数也不依赖于类的对象。我们被允许使用对象和'.'来调用静态成员函数。但建议使用类名和范围解析运算符调用静态成员。

  允许静态成员函数**仅访问静态数据成员或其他静态成员函数**，它们无法访问类的非静态数据成员或成员函数。

### 3.static限定访问范围

```c++
// source1.cpp
extern void sayHello();
const char* msg = "Hello World!\n";
int main()
{
    sayHello();
    return 0;
}

// source2.cpp
#include <cstdio>
extern char* msg;
void sayHello()
{
    printf("%s", msg);
}
```

g++对于上面两个代码文件是可以正常编译并且打印Hello World!，但如果给source1.cpp中的msg加上static，则会导致undefined reference to 'msg'的编译错误。

```c++
// source1.cpp
extern void sayHello();
static const char* msg = "Hello World!\n";
int main()
{
    sayHello();
    return 0;
}
```



END