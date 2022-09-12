---
layout: post
title:  "Overleaf里的基本语法（2）"
date:   2021-08-02
excerpt: "本篇主要记录公式中的语法."
tag:
- 随笔 
- Overleaf
comments: false
---





<center><b>熟练使用Overleaf.</b> </center>

# Overleaf基本语法（2）

#### 1.插入公式

插入行间公式：`$x+y=z$`

插入段间公式：`$$x+y=z$$`或

```latex
\begin{equation}
x + y = z
\end{equation}
```

效果如下：

![](https://gitee.com/llesssssa/imagebed/raw/master/charugongshi.png)

#### 2.大括号表示包含

```latex
\begin{equation}
    \mathcal{A}=\left\{\mathcal{B},\mathcal{C}\right\}
\end{equation}
```

效果：

![](https://gitee.com/llesssssa/imagebed/raw/master/baohan.png)

#### 3.上下角标以及分数

```latex
\begin{equation}
    a^{b}=c-d^{-\sfrac{1}/{2}}ef^{-\sfrac{1}/{2}}
\end{equation}
```

次幂用^符号，分数用`\sfrac`或者`\frac`都可。

效果：

![](https://gitee.com/llesssssa/imagebed/raw/master/fenshu.png)

#### 4.求和公式

```latex
\begin{equation}
    A_{ij}=\sum_{j=0}^{n-1}B_{ij}
\end{equation}
```

效果：

![](https://gitee.com/llesssssa/imagebed/raw/master/qiuhe.png)

#### 5.分段公式

```latex
$$ A_{ij}=\left\{
\begin{aligned}
1 & , & in \\
0 & , & otherwise \\
\end{aligned}
\right.
$$
```

效果：

![](https://gitee.com/llesssssa/imagebed/raw/master/fenduan.png)

#### 6.遇到的小问题 解决

使用`\begin{aligned}`出现Environment aligned undefined.

解决：在`\begin{document}`之前加上：

`\usepackage{amsmath}`

即可。

Overleaf官网也有很多案例解决，遇到问题可以直接搜索。如下图：

![](https://gitee.com/llesssssa/imagebed/raw/master/overleafwenti.png)



END