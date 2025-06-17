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

## 1. 基本语法

### 1.1 标题

标题即井号（`#`）加一个空格，`#`的数量代表标题的级别。

```markdown
# Heading level 1

## Heading level 2

### Heading level 3

#### Heading level 4

##### Heading level 5

###### Heading level 6
```

### 1.2 段落

段落即用空白行将一行或多行文本进行分割。

```markdown
This is the first paragraph.

And this is the second paragraph.
```

👉 渲染效果如下：

This is the first paragraph.

And this is the second paragraph.

### 1.3 换行

行尾添加“结尾空格”或用 HTML 的`<br>`标签来实现换行。

```html
<p>This is the first line.</p>
<br />
<p>And this is the second line.</p>
```

👉 渲染效果如下：

This is the first line.<br>And this is the second line.

### 1.4 强调

① **粗体**：在字符两侧各添加两个星号（`**`）。

② _斜体_：在字符两侧各添加一个星号（`*`）。

```markdown
This is bold **emphasis**.
This is italic _emphasis_.
This is bold and italic **_emphasis_**.
```

👉 渲染效果如下：

This is bold **emphasis**. This is italic _emphasis_.

This is bold and italic **_emphasis_**.

### 1.5 引用

① 单段引用：右尖括号（ `>` ）加一个空格。

② 多段引用：段落间插入单独的右尖括号（ `>` ）。

③ 嵌套引用：嵌套一级，增加一个右尖括号（ `>` ）数量，后加一个空格。

④ 混合元素引用：每行前加右尖括号（ `>` ）。

```markdown
> This is a block quote.
> This is a block quote with other elements.
>
> > - This is the first item in the unordered list.
> > - This is the second item in the unordered list.
> >   This is _italic_. This is **bold**.
```

👉 渲染效果如下：

> This is a block quote with other elements.
>
> > - This is the first item in the unordered list.
> > - This is the second item in the unordered list.
>
> This is _italic_. This is **bold**.

### 1.6 列表

① 有序列表（`1. `）：数字加一个英文句点（`.`），再加一个空格。

② 无序列表（`- `）：短横线（`-`）或星号（`*`）或加号（`+`）加一个空格。

③ 嵌套列表（`   -`）：缩进四个空格或一个制表符。

```markdown
1. First item
2. Second item
   > blockquote
3. Third item
   - Indented item
   - Indented item
```

👉 渲染效果如下：

1. First item

2. Second item

   > A blockquote would look great below the second list item.

3. Third item

   - Indented item
   - Indented item

### 1.7 代码

① 行内代码：用单反引号（`` `）包裹内容。

② 行内含反引号的代码：用双反引号（` `` ` ）包裹内容。

③ 代码块：用两对三个反引号（` ``` `）包裹段落。

````markdown
At the command prompt, type `nano`.
`` Use `code` in your Markdown file. ``

```bash
hugo verson
```
````

👉 渲染效果如下：

At the command prompt, type `nano`.`` Use `code` in your Markdown file. ``

```bash
hugo version
```

### 1.8 分割线

单独行连续三个或多个星号（`***`）、短横线（`---`）或下划线（`___`），且行内无其他内容，然后按回车。

```markdown
---
---

---
```

### 1.9 链接

① 超链接：链接文本放在中括号内，链接地址放在后面的括号中，链接 title 可选。

② URL 和 Email：用一对尖括号（`<> `）包裹内容。

③ 带格式的链接：强调链接用星号（`*`）包裹连接；方括号内添加反引号（`` `）表示将链接表示为代码。

④ 引用样式链接（如尾注或脚注）：第一部分用两组方括号设置，链接文本放在第一组方括号，标签放在第二组方括号，用于指向链接的位置；第二部分包括放在方括号中的标签和一个冒号，方括号前面不允许有字符，链接和链接 title 可选，链接可以放在尖括号内，链接 title 放在双引号、单引号或括号内。

```markdown
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

### 1.10 图片

① 普通图片：感叹号（`!`）加方括号（`[]`）加圆括号，其中替代文本放在方括号内，图片链接和图片标题放在圆括号内。

② 链接图片：普通图片语法放在方括号内，链接地址放在圆括号内。

```markdown
![panda1](pic1-1.png "大熊猫1")
[![panda2](pic1-2.png "大熊猫2")](http://zyyaria.github.io)
```

👉 渲染效果如下：

![panda1](pic1-1.png "大熊猫1")

[![panda2](pic1-2.png "大熊猫2")](http://zyyaria.github.io)

### 1.11 转义字符

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

```markdown
\* Without the backslash, this would be a bullet in an unordered list.
```

👉 渲染效果如下：

\* Without the backslash, this would be a bullet in an unordered list.

② 特殊字符自动转义：`&`在非 HTML 实体中自动转义为`&amp;`，比如`AT&T`必须写成`AT&amp;T`，但`&copy;`（著作权的符号）保留原样；`<`在非 HTML 实体中自动转义为`&lt;`，比如`4 < 5`必须写成`4 &lt; 5`，但`<div>`（HTML 标签）保留原样。另外，它们在代码块内不受转义影响。

### 1.12 内嵌 HTML 标签

① 行级内联标签：如 `<span>`、`<cite>`、`<del>`，直接在段落、列表或标题内使用。

② 区块标签：如 `<div>`、`<table>`、`<pre>`、`<p> `，必须在前后加上空行，便于内容区分，且这些元素的开始和结尾不能用 tab 或空格来缩进。

```markdown
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

## 2. 扩展语法

扩展语法是否可用取决于 Markdown 应用程序是否支持。

### 2.1 表格

## 参考内容

[Markdown 官方教程](https://markdown.com.cn/)
