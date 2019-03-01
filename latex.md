# LateX
###### Atom (Ctrl+Alt+B)
###### 推荐学习链接:
> https://liam.page/2014/09/08/latex-introduction/
## Hello, LateX! (英文)
```
\documentclass{article}
% 这里是导言区(对整篇文档进行设置)
\begin{document}
Hello, LateX!
\end{document}
```
## 你好, LateX! (中英混编)
```
\documentclass[UTF8]{ctexart}
\begin{document}
你好, LateX!
\end{document}
```
## 模板
```
\documentclass[UTF8]{ctexart}
\title{主题}
\author{作者}
\date{时间}
\usepackage{amsmath}
\begin{document}
\maketitle
\tableofcontents
\section{章节}
主题中的内容
\subsection{亚章节}
\subsubsection{亚亚章节}
\paragraph{段落}
段落内容
\subparagraph{亚段落}
亚段落内容

添加行内公式:$inline$

添加行间公式:

\[display\]

\begin{equation}
display with number
\end{equation}
\end{document}
```
## 语法
### 控制序列(全局)

| `\`(开头)  | `控制序列` | `{ }` | `{成分名}` | 功能 |
|:---:|:---:|:---:|:---:|:---:|
| `\` | `documentclass` | `{article}` | `{参数}` | 调用名为`article`的文档类 |
| `\` | `date` | `{time}` | `{时间}` | 设置时间 **时间:自定义 或 `\today`** |
| `\` | `usepackage` | `{amsmath}` | `{宏包}` | 加载名为`amsmath`的宏包**(用于插入数学公式)** |
| `\` | `begin` +  `end` | `{document}` `{equation}` | `{环境名}` | 在`环境名`环境中的内容被正常的输出到文档中**(document环境中可输出到文档中,equation环境中可对行间公式进行编号)** |
| `\` | `maketitle` |  |  | 将在导言区中定义的内容按照预定的格式展现出来 |
| `\` | `tableofcontents` |  |  | **添加目录** |
| `\` | `` | `{}` | `{}` |  |
| `\` | `` | `{}` | `{}` |  |
### 控制序列(数学)
| `\控制序列{·}` | 功能 |
| :------------- | :------------- |
| `\sqrt{·}` | 根式 |
| `\frac{·}{··}` | ·(分子)，··(分母) |
| `\pm` | ± |
| `\times` | × |
| `\div` | ÷ |
| `\cdot` | · |
| `\cap` | ∩ |
| `\cup` | ∪ |
| `\geq` | ≥ |
| `\leq` | ≤ |
| `\neq` | ≠ |
| `\approx` | ≈ |
| `\equiv` | ≡ |
#### 其他
##### 分数
```
$\frac{inline}{size}$ (默认)
$\dfrac{display}{size}$

\[\frac{display}{size}\](默认)

\[\tfrac{inline}{size}\]
```
##### 连加、连乘、极限、积分
```
$ \sum_{i=1}^n i\quad \prod_{i=1}^n $ 连加+连乘

$ \sum\limits_{i=1}^n i\quad \prod\limits_{i=1}^n $ 连加+连乘(压缩)

\[ \lim_{x\to0}x^2 \quad \int_a^b x^2 dx \] 极限(默认压缩)+微积分

\[ \lim\nolimits_{x\to0}x^2\quad \int\nolimits_a^b x^2 dx \]
极限(不压缩)+微积分(不压缩)

\[ \iint\quad \iiint\quad \iiiint\quad \idotsint \]
多重积分
```
##### 定界符(括号等)
```
\[ \Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr) \]
\[ \Biggl[\biggl[\Bigl[\bigl[[x]\bigr]\Bigr]\biggr]\Biggr] \]
\[ \Biggl \{\biggl \{\Bigl \{\bigl \{\{x\}\bigr \}\Bigr \}\biggr \}\Biggr\} \]
\[ \Biggl\langle\biggl\langle\Bigl\langle\bigl\langle\langle x
\rangle\bigr\rangle\Bigr\rangle\biggr\rangle\Biggr\rangle \]
\[ \Biggl\lvert\biggl\lvert\Bigl\lvert\bigl\lvert\lvert x
\rvert\bigr\rvert\Bigr\rvert\biggr\rvert\Biggr\rvert \]
\[ \Biggl\lVert\biggl\lVert\Bigl\lVert\bigl\lVert\lVert x
\rVert\bigr\rVert\Bigr\rVert\biggr\rVert\Biggr\rVert \]
```
##### 省略号
```
\[ x_1,x_2,\dots ,x_n\quad 1,2,\cdots ,n\quad
\vdots\quad \ddots \]
```
##### 矩阵
```
\[ \begin{pmatrix} a&b\\c&d \end{pmatrix} \quad
\begin{bmatrix} a&b\\c&d \end{bmatrix} \quad
\begin{Bmatrix} a&b\\c&d \end{Bmatrix} \quad
\begin{vmatrix} a&b\\c&d \end{vmatrix} \quad
\begin{Vmatrix} a&b\\c&d \end{Vmatrix} \]
```
###### 行内小矩阵
```
$ ( \begin{smallmatrix} a&b\\c&d \end{smallmatrix} ) $
```
##### 长公式
###### 不对齐
```
\begin{multline}
x = a+b+c+{} \\
d+e+f+g
\end{multline}
```
###### 对齐
```
\[\begin{aligned}
x ={}& a+b+c+{} \\
&d+e+f+g
\end{aligned}\]
```
##### 公式组
```
\begin{gather}
a = b+c+d \\
x = y+z
\end{gather}
\begin{align}
a &= b+c+d \\
x &= y+z
\end{align}
```
##### 分段函数
```
\[ y= \begin{cases}
-x,\quad x\leq 0 \\
x,\quad x>0
\end{cases} \]
```
### 注释
`%注释` (输出`%`需要使用`\%`转义)
## P.S.
| 功能 | 实现 |
| :------------- | :------------- |
| 换行 | `\\` |
| 幂**(仅作用于之后的一个字符,使用`{连续字符}`)** | `^` |
