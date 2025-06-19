---
title: "Program Markdown Grammar"
description: "Program Markdown Grammar"
date: 2025-06-18T00:54:54+08:00
lastmod: 2025-06-18T00:54:54+08:00
categories: ["程序"]
collections: ["Hugo 博客"]
draft: true
---

<!--more-->

Markdown 是一种纯文本排版工具，通过简单符号（如 `#` 标题 / `-` 列表）实现博客、笔记的秒级格式化，让作者专注内容创作而非样式调整。

下面内容以一个`text`文本+一个渲染结果记录。

## 1. 段落级语法（文档结构）

### 标题

语法：`# 标题`（1~6个`#`，后跟空格）

要点：`#`数量=标题级别（`#`=H1，`######`=H6）

```text
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

### 列表

有序列表：`1. 内容`（自动序号，数字后必须带`.`和空格）

无序列表：`- 项`/`* 项`/`+ 项`（符号后必须空格）

任务列表：`- [ ] 未完成`/`- [x] 完成`（方括号内需空格）

嵌套列表：子项缩进 **4空格**（如父项下空4格写`- 子项`）

```text
1. 第一项
    - [x] 第一项已完成的元素
    - [ ] 第一项未完成的元素
3. 第二项
    > 第二项的引用块
4. 第三项
    - 第三项嵌套的第一个元素
    - 第三项嵌套的第二个元素
```

1. 第一项
    - [x] 第一项已完成的元素
    - [ ] 第一项未完成的元素
3. 第二项
    > 第二项的引用块
4. 第三项
    - 第三项嵌套的第一个元素
    - 第三项嵌套的第二个元素

### 表格

表格的列用`|`来分隔，表头和其他行用`-`来分隔。

```text
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
```

| 表头   | 表头   |
| ------ | ------ |
| 单元格 | 单元格 |
| 单元格 | 单元格 |

### 引用块

区块引用是在段落开头用`>`符号，后面紧跟一个空格符号。一个`>`是最外层，两个`>`是第一层嵌套，以此类推可创建多级嵌套引用。

```text
> 这是引用的第一行。
> 这是引用的第二行。
>
>> - 第一层嵌套
>>> - 第二层嵌套
> 
> 这是引用的**第二段**。
```

> 这是引用的第一行。
> 这是引用的第二行。
>
> > - 第一层嵌套
> >
> > > - 第二层嵌套
>
> 这是引用的**第二段**。

### 代码块

代码区块用4个空格或一个制表符（`Tab`键）来创建，或者用两组三个反引号（`` `）包裹一段代码，并指定一种语言（可选）。其中，后者添加语言标识符可以启用语法高亮功能。

~~~text
① 缩进式代码块：
	hugo version
	hugo server
	
② 三反引号代码块：
```bash
hugo version
hugo server
```
~~~

```bash
hugo version
hugo server
```

### 公式块

数学公式用 `$` 符号包裹区域，通过 `_` 下标、`^` 上标、`\` 开头的命令（如 `\frac`）等 LaTeX 语法来书写。

```text
$$
\begin{align}
f(x) &= ax^2 + bx + c \\
f'(x)  &= 2ax + b \\
f''(x)  &= 2a
\end{align}
$$
```

$$
\begin{align}
f(x) &= ax^2 + bx + c \\
f'(x)  &= 2ax + b \\
f''(x)  &= 2a
\end{align}
$$

### 脚注和链接引用？？

### 分割线

单独一行用三个以上`*`、`-`或`_`来创建，且行内无其他内容。

```text
***
---
___
```

## 2. 格式级语法（文本修饰）

### 强调

① **粗体**语法：用两个`*`或`_`来包围文字。

② _斜体_语法：用一个`*`或`_`来包围文字。

③ ***粗斜体***结合：用三个`*`或`_`来包围文字。

```text
This is bold **emphasis**.
This is bold __emphasis__.
This is italic *emphasis*.
This is italic _emphasis_.
This is bold and italic ***emphasis***.
This is bold and italic ___emphasis___.
```

This is bold **emphasis**. 

This is italic _emphasis_. 

This is bold and italic **_emphasis_**.

### 下划线

下划线用HTML的`<u>`标签来实现。

```text
<u>This is underlined text.</u>
```

<u>This is underlined text.</u>

### 行内代码

① 基本语法：用一个`` `来包围代码。

② 包含反引号的代码：用两个`` `来包围代码。

````text
At the command prompt, type `nano`.
`` Use `code` in your Markdown file. ``
`` `` ``
````

At the command prompt, type `nano`.

`` Use `code` in your Markdown file. ``

### 内联公式

行内公式用 `$` 符号来包围，公式会嵌入文本中。

```text
文本中的变量 $x = 5$ 和函数 $f(x) = x^2 + 2x + 1$。
```

文本中的变量 $x = 5$ 和函数 $f(x) = x^2 + 2x + 1$。

### 删除线

删除线用两个波浪线（`~`）来包围文字。

```text
~~This is content to be deleted.~~
```

~~This is content to be deleted.~~

### 高亮

文本高亮不是标准 Markdown 语法，部分平台支持。文本高亮用两`==`来包围文字。

```text
This is ==highlighted== text.
```

## 2.5 脚注

脚注是对文本的补充说明，分为两部分：第一部分创建脚注参考，第二部分说明脚注内容。

```text
This is the text that needs to be noted.[^what]
[^what]:Here is the explanation of the noted content.
```

👉 渲染效果如下：

This is the text that needs to be noted.[^what]
[^what]:Here is the explanation of the noted content.

### 2.8 段落和换行

Markdown 段落是文本的基本单位，由一个或多个连续的文本行组成。段落的换行是使用两个以上空格加上回车。

要在不创建新段落的情况下换行，就在行尾添加两个或更多空格，然后按回车，或者使用HTML的`<br>`标签来实现。

```text
This is the first paragraph.

This is the first line.<br>And this is the second line.

And this is the second paragraph.
```

👉 渲染效果如下：

This is the first paragraph.

This is the first line.<br>And this is the second line.

And this is the second paragraph.

## 9. 链接

① 超链接：链接文本放在中括号内，链接地址放在后面的括号中，链接 title 可选。

② URL 和 Email：用一对尖括号（`<> `）包裹内容。

③ 带格式的链接：强调链接用星号（`*`）包裹连接；方括号内添加反引号（`` `）表示将链接表示为代码。

④ 引用样式链接（如尾注或脚注）：第一部分用两组方括号设置，链接文本放在第一组方括号，标签放在第二组方括号，用于指向链接的位置；第二部分包括放在方括号中的标签和一个冒号，方括号前面不允许有字符，链接和链接 title 可选，链接可以放在尖括号内，链接 title 放在双引号、单引号或括号内。

```text
[Link text](http://example.com "link title")
<http://example.com>
<fake@example.com>
**[Link text](http://example.com "link title")**
_[Link text](http://example.com "link title")_
[`code`](#code)

引用样式链接：
第一部分：[链接文本][label]
[label]:<http://example.com> (link title)
```

👉 渲染效果如下：

[Link text](http://example.com "link title")

<http://example.com> <fake@example.com>

**[Link text](http://example.com "link title")** _[Link text](http://example.com "link title")_ [`code`](#code)

第一部分：[链接文本][label]

[label]: http://example.com "link title"

## 10. 图片

① 普通图片：感叹号（`!`）加方括号（`[]`）加圆括号，其中替代文本放在方括号内，图片链接和图片标题放在圆括号内。

② 链接图片：普通图片语法放在方括号内，链接地址放在圆括号内。

```text
![panda1](pic1-1.png "大熊猫1")
[![panda2](pic1-2.png "大熊猫2")](http://zyyaria.github.io)
```

👉 渲染效果如下：

![panda1](pic1-1.png "大熊猫1")

[![panda2](pic1-2.png "大熊猫2")](http://zyyaria.github.io)

## 11. 转义字符

① 可做转义的字符：转义字符是通过反斜杠字符（`\`）让 Markdown 的语法符号（如 `*` `#` `>`）变成普通文本显示出来，避免被误解析为格式。

| 字符 | 作用        | 转义写法  | 未转义后果       |
| ---- | ----------- | --------- | ---------------- |
| `\`  | 转义符本身  | `\\`      | 可能中断解析     |
| `` ` | 代码边界    | `` \`  `` | 意外结束代码块   |
| `*`  | 强调/列表   | `\*`      | 变成粗体/列表项  |
| `_`  | 强调        | `\_`      | 意外斜体         |
| `#`  | 标题        | `\#`      | 意外生成标题     |
| `>`  | 引用        | `\>`      | 意外引用块       |
| `-`  | 列表/分割线 | `\-`      | 意外生成列表项   |
| `+`  | 列表        | `\+`      | 意外生成列表项   |
| `[`  | 链接起始    | `\[`      | 意外开始链接解析 |

```text
\* Without the backslash, this would be a bullet in an unordered list.
```

👉 渲染效果如下：

\* Without the backslash, this would be a bullet in an unordered list.

② 特殊字符自动转义：`&`在非 HTML 实体中自动转义为`&amp;`，比如`AT&T`必须写成`AT&amp;T`，但`&copy;`（著作权的符号）保留原样；`<`在非 HTML 实体中自动转义为`&lt;`，比如`4 < 5`必须写成`4 &lt; 5`，但`<div>`（HTML 标签）保留原样。另外，它们在代码块内不受转义影响。

## 12. 内嵌 HTML 标签

① 行级内联标签：如 `<span>`、`<cite>`、`<del>`，直接在段落、列表或标题内使用。

② 区块标签：如 `<div>`、`<table>`、`<pre>`、`<p> `，必须在前后加上空行，便于内容区分，且这些元素的开始和结尾不能用 tab 或空格来缩进。

```text
This **word** is bold. This <em>word</em> is italic.
This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

This is another regular paragraph.
```

👉 渲染效果如下：

This **word** is bold. This <em>word</em> is italic.

This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>
This is another regular paragraph.

[Markdown 官方教程](https://markdown.com.cn/)
