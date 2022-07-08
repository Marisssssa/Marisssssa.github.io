---
layout: post
title:  "C++05.c与c++互相函数调用"
date:   2022-05-31
excerpt: "cpp.c与c++互相函数调用"
tag:
- C++
- C与C++互相函数调用
comments: false
---

<center><b>05.c与c++互相函数调用.</b> </center>

# C++05.c与c++互相函数调用

### 1.C++调用C函数

```c++
//xx.h
extern int add(...)

//xx.c
int add(){
    
}

//xx.cpp
extern "C" {
    #include "xx.h"
}
```

### 2.C调用C++函数

```c++
//xx.h
extern "C"{
    int add();
}
//xx.cpp
int add(){
    
}
//xx.c
extern int add();//头文件处调用
```

与C++调用C接口不同，C++确实是能够调用编译好的C函数，而这里C调用C++，不过是把C++代码当成C代码编译后调用而已。也就是说，C并不能直接调用C++库函数。



END