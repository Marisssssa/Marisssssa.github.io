---
layout: post
title:  "Overleaf里的基本语法（1）"
date:   2021-08-01
excerpt: "熟练使用，论文写的更快."
tag:
- 随笔 
- Overleaf
comments: false
---





<center><b>熟练使用Overleaf.</b> </center>

# Overleaf基本语法（1）

#### 1.各级标题

**一级标题：**`\section{Title level1}`

**二级标题：**`\subsection{Title level2}`

**三级标题：**`\subsubsection{Title level3}`

效果图：

![](https://gitee.com/llesssssa/imagebed/raw/master/1.png)

#### 2.引用

在百度学术获取要引用的论文的引用信息，复制到bib文件中，如下图：

![](https://gitee.com/llesssssa/imagebed/raw/master/bibwenjian.png)

在tex文中添加`[\cite{2016Stacked}`即可引用。

#### 3.加粗

`\textbf{Data}`

效果如下：

<img src="https://gitee.com/llesssssa/imagebed/raw/master/bf.png" style="zoom:150%;" />

#### 4.表格

**三线式表格**

```latex
\begin{table*}[!t]
% increase table row spacing, adjust to taste
\renewcommand{\arraystretch}{1.3}
\caption{myTable}%标题
\label{table_3}
\centering%使得表格居中
\begin{tabular}{llll}%列的设定
\toprule
 &C1 & C2 & C3  \\
\midrule
L1 &- &- &-   \\
L2  &- &- &- \\
L3  &- &- &- \\
L4 &- &- &- \\
L5 &- &- &- \\
\bottomrule
\end{tabular}
\end{table*}
```

效果图：

![](https://gitee.com/llesssssa/imagebed/raw/master/biaoge.png)

**合并单元格**

```latex
\begin{table}
\centering
\caption{myTable.}\label{tab1}
\begin{tabular}{|l|l|l|}
\hline
&\multicolumn{2}{c}{Combine}   \\
\hline
 &C1&C2\\
\hline
L1 &- &-\\
L2  &- &- \\
\hline
\end{tabular}
\end{table}
```

效果图：

![](https://gitee.com/llesssssa/imagebed/raw/master/hebing.png)

横向合并用`\multicolumn{}{}{}`

纵向合并用`\multirow{}{}{}`

#### 5.插入图片

上传自己要用的图片。

![](https://gitee.com/llesssssa/imagebed/raw/master/cimuselect.jpg)

然后插入：

```latex
\begin{figure}[htp]
\begin{center}
\includegraphics[width=1.0\textwidth]{cimu.JPG}
\caption{Cimu.}\label{fig:total}
\end{center}
\end{figure}
```

插入效果图：

![](https://gitee.com/llesssssa/imagebed/raw/master/charujieguo.png)

#### 6.其他

**换行：**`\newline`

**居中：**`\center`

**斜体：**`\emph`或者`\textit`

**下划线：**`\underline`

**缩进：**`\indent`