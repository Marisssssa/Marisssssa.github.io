---
layout: post
title:  "C++06.struct与class"
date:   2022-05-31
excerpt: "cpp.struct与class"
tag:
- C++
- struct
- class
comments: false
---

<center><b>06.struct与class.</b> </center>

# C++06.struct与class

### 一、C中struct

- 在C中struct只单纯的用作**数据的复合类型**，也就是说，在结构体声明中只能将数据成员放在里面，而**不能将函数放在里面**。

- 在C结构体声明中不能使用C++访问修饰符，如：public、protected、private 而在C++中可以使用。

- 在C中定义结构体变量，如果使用了下面定义必须加struct。

- C的结构体不能继承（没有这一概念）。

- 若结构体的名字与函数名相同，可以正常运行且正常的调用！例如：**可以定义与 struct Base 不冲突的 void Base() {}**。

  ```c++
  #include<stdio.h>
  
  struct Base {            // public
      int v1; 
  //    public:      //error
          int v2; 
      //private:
          int v3; 
      //void print(){       // c中不能在结构体中嵌入函数
      //    printf("%s\n","hello world");
      //};    //error!
  };
  
  void Base(){
      printf("%s\n","I am Base func");
  }
  //struct Base base1;  //ok
  //Base base2; //error
  int main() {
      struct Base base;
      base.v1=1;
      //base.print();
      printf("%d\n",base.v1);
      Base();
      return 0;
  }
  ```

### 二、C++中struct

- C++结构体中不仅可以定义数据，还可以定义函数。
- C++结构体中可以使用访问修饰符，如：public、protected、private 。
- C++结构体使用可以直接使用不带struct。
- C++继承
- 若结构体的名字与函数名相同，可以正常运行且正常的调用！但是定义结构体变量时候只能用带struct的！

```c++
#include<iostream>
#include<stdio.h>

struct Base {         
    int v1;
//    private:   //error!
        int v3;
    public:     //显示声明public
        int v2;
    void print(){       
        printf("%s\n","hello world");
    };    
};

int main() {
    struct Base base1;  //ok
    Base base2; //ok
    Base base;
    base.v1=1;
    base.v3=2;
    base.print();
    printf("%d\n",base.v1);
    printf("%d\n",base.v3);
    return 0;
}
```

### 三、struct和class区别

struct 更适合看成是一个**数据结构**的实现体，class 更适合看成是一个**对象**的实现体。

**区别:**

最本质的一个区别就是**默认的访问控制**

默认的继承访问权限。struct 是 public 的，class 是 private 的。

struct 作为数据结构的实现体，它默认的数据访问控制是 public 的，而 class 作为对象的实现体，它默认的成员变量访问控制是 private 的。



END