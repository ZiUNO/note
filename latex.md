# LateX
## Atom (Ctrl+Alt+B)
## 推荐学习链接:
> https://liam.page/2014/09/08/latex-introduction/
## Hello, LateX!(英文)
```
\documentclass{article}
% 这里是导言区(对整篇文档进行设置)
\begin{document}
Hello, LateX!
\end{document}
```
## 你好, LateX!(中英混编)
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
\usepackage{graphicx}
\usepackage{fancyhdr}
\pagestyle{fancy}
\lhead{\author}
\chead{\date}
\rhead{xxxxxxxxx}
\lfoot{}
\cfoot{\thepage}
\rfoot{}
\renewcommand{\headrulewidth}{0.4pt}
\renewcommand{\headwidth}{\textwidth}
\renewcommand{\footrulewidth}{0pt}
\usepackage{setspace}
\onehalfspacing
\addtolength{\parskip}[.4em]
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

行内公式:$inline$

行间公式:

\[display\]

\begin{equation}
display with number
\end{equation}

图片:

\includegraphics{test.jpg}

图片(压缩至页面宽度的80\%)

\includegraphics[width = .8\textwidth]{test.jpg}

表格:

\begin{tabular}{|l|c|r|}
  \hline
  居左l& 居中c& 居右r\\
  \hline
  -& -& -\\
  \hline
\end{tabular}

浮动体:

\begin{figure}[htbp]
\centering
\includegraphics{test.jpg}
\caption{图片标题}
\end{figure}

\end{document}
```
## 语法

### 控制序列(全局)
| `\`(开头)  | `控制序列` | `{ }` | `{成分名}` | 功能 |
|:---:|:---:|:---:|:---:|:---:|
| `\` | `documentclass` | `{article}` | `{参数}` | 调用名为`article`的文档类 |
| `\` | `date` | `{time}` | `{时间}` | 设置时间 **时间:自定义 或 `\today`** |
| `\` | `usepackage` | `{amsmath}` `{graphicx}` `{geometry}` `{fancyhdr}` `{setspace}`  | `{宏包名}` | 加载指定宏包(**amsmath用于插入数学公式,graphicx用于插入图片,geometry用于设置页边距,fancyhdr用于设置页眉页脚,setspace用于设置行、段间距**)  |
| `\` | `begin` +  `end` | `{document}` `{equation}` `{tabular}` `{figure}[htbp]` | `{环境名}` | 在`环境名`环境中的内容被正常的输出到文档中(**document环境中可输出到文档中,equation环境中可对行间公式进行编号,tabular环境中添加表格,figure环境中添加浮动体(自动调整位置[h-here,t-top,b-bottom,p-float page])**) |
| `\` | `maketitle` |  |  | 将在导言区中定义的内容按照预定的格式展现出来 |
| `\` | `tableofcontents` |  |  | **添加目录** |
| `\` | `includegraphics` | `{.jpg}` | `{图片名}` | **添加图片(同目录)** |
| `\` | `hline` |  |  | tabular环境中表示表格的横线 |
| `\` | `centering` |  |   | **figure环境中插图居中** |
| `\` | `caption` | `{name}` | `{插图标题}` | 添加插图名(自动编号) |
| `\` | `label` | `{fig:photo}` | `{标签名}` | 为浮动体添加标签(应位于标题命令后) |
| `\` | `geometry` | `{···}` | `{页边距设置}` | 用于设置**页边距和纸张大小** |
| `\` | `pagestyle` | `{fancy}` | `{风格名}` | 页面应用指定风格 |
| `\` | `onehalfspacing` |  |  | setspace包中**设置1.5倍行距** |
| `\` | `addtolength` | `{\parskip}` | `{增加长度的位置}[.Nem]` | 增加段间隔N个em(N可正可负)|
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
| :-------------: | :-------------: |
| 换行 | `\\` |
| 幂(**仅作用于之后的一个字符,使用`{连续字符}`**) | `^` |
