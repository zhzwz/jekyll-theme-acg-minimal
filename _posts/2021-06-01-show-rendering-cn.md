---
title: Markdown 语法的渲染效果展示页
description: 详细展示 Jekyll Theme ACG 主题对于 Markdown 语法的渲染效果，以及介绍该主题独有的特性与使用方式。
categories: guide
tags: markdown theme chinese
color: red
pin: true
---

-----

- 简体中文指南 \| [English Guide]({{ site.url }}/2021/06/01/show-rendering-en)

我的英语水平不高，如果在英文指南的内容中遇到错误或偏，请以中文指南的内容为准。


## 简介

> Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成有效的 HTML 文档。
>
> 由于 Markdown 的轻量化、易读易写特性，甚至对于图片、图表、数学公式都有支持，目前许多网站都广泛使用 Markdown 来撰写帮助文档，或是用于论坛上发表消息。
>
> —— [维基百科](https://zh.wikipedia.org/wiki/Markdown)
> {: class="text-right" }

Github 支持的 Markdown 语法标准被称为 [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown)，简称 GFM。Jekyll Theme ACG 主题在 GFM 的语法之外还支持一些其他的特性与使用方式。

## Front Matter

每篇文章都必须在开头使用 YAML 格式的 Front Matter。

Front Matter 会使文件被 Jekyll 识别为特殊文件，Front Matter 的内容将会被绑定为这篇文章的独有属性。

例如，下面就是这篇文章的 Front Matter：

```
---
title: Markdown 语法的渲染效果展示页
description: 详细展示 Jekyll Theme ACG 主题对于 Markdown 语法的渲染效果，以及介绍该主题独有的特性与使用方式。
categories: guide
tags: markdown theme chinese
color: red
pin: true
---
```

### title

文章的标题。

如果没有手动设置 title 值，那么 Jekyll 将会使用文件名生成一个 title 值。例如这篇文章的文件名是 `2021-06-01-show-rendering-cn.md`，自动生成的标题为 `Show Rendering Cn`，通常应该避免这种情况。

### description

文章的简述。

如果没有手动设置 description 的值，那么 Jekyll 将会自动提取文章的开头生成一个 description 值。

### categories

文章的分类。

如果一篇文章有多个分类，分类名称之间使用空格分割。

### tags

文章的标签。

如果一篇文章有多个标签，标签名称之间使用空格分割。

### color

文章的主题色。

如果没有手动设置 color 的值，那么 Jekyll 将会读取配置文件 `_config.yml` 中的 color 值。

### pin

文章置顶选项。

如果没有手动设置 pin 的值，那么本篇文章就不会在首页置顶。

## 列表

### 无序列表

- 输入：

```
- A
  - a
    - i
    - ii
  - b
    - I
    - II
- B
```

- 输出：

- A
  - a
    - i
    - ii
  - b
    - I
    - II
- B

### 有序列表

- 输入：

```
1. A
   1. a
   1. b
   1. c
2. B
3. C
```

- 输出：

1. A
   1. a
   1. b
   1. c
2. B
3. C

> 无序的数字会自动变为有序。

### 待办列表

- 输入：

```
- [x] 待办一
- [ ] 待办二
- [x] 待办三
- [ ] 待办四
```

- 输出：
- [x] 待办一
- [ ] 待办二
- [x] 待办三
- [ ] 待办四


## 表格

### 标准表格

- 输入：

<pre><code class="language-markdown"># 标准 Markdown 语法中的表格示例
| Column A | Column B | Column C |
| :------- | :<span>------</span>: | -------: |
|   Left   |  Center  |  Right   |
|    A     |    B     |    C     |
</code></pre>

- 输出：

| Column A | Column B | Column C |
| :------- | :------: | -------: |
|   Left   |  Center  |  Right   |
|    A     |    B     |    C     |

### 忽略表头与对齐方式

与标准的 Markdown 语法不同，表格的表头与对齐方式可以省略。

- 输入：

```
| 1 | 2 | 3 |
| 4 | 5 | 6 |
| 7 | 8 | 9 |
```

- 输出：

| 1 | 2 | 3 |
| 4 | 5 | 6 |
| 7 | 8 | 9 |

### 自定义对齐方式

- 输入：

<pre><code class="language-markdown"># 每个单元格都可以使用 `:` 控制自身的对齐方式。
| ########## | ########## | ########## |
|:   Left    |:  Center  :|   Right   :|
|:  Center  :|   Right   :|:   Left    |
|   Right   :|:   Left    |:  Center  :|
</code></pre>


- 输出：

| ########## | ########## | ########## |
|:   Left    |:  Center  :|   Right   :|
|:  Center  :|   Right   :|:   Left    |
|   Right   :|:   Left    |:  Center  :|

### 合并表格列

- 输入：

<pre><code class="language-markdown"># 在 `||` 之间所表示的单元格，将被合并。
| 1 | 2 | 3 |
|: 45 :|<b></b>| 6 |
|: 789   :|<b></b>|<b></b>|
</code></pre>

- 输出：

| 1 | 2 | 3 |
|: 45 :|| 6 |
|: 789   :|||

### 合并表格行

- 输入：

<pre><code class="language-markdown"># 以 `^^` 开头的单元格，将被合并。
| 1 | 2 |  3  |
| 4  5 |<b></b>|^^ 6 |
|^^ 7 8|<b></b>|  9  |
</code></pre>

- 输出：

| 1 | 2 |  3  |
| 4  5 ||^^ 6 |
|^^ 7 8||  9  |


## 代码

### 单行代码

- 输入：``` `const name = "jekyll-theme-acg";` ```

- 输出：`const name = "jekyll-theme-acg";`

### 多行代码

- 输入：

<pre><code class="language-markdown">```javascript
function print() {
  console.log("Hello world.");
}
print(); // Hello world.
```</code></pre>

- 输出：

```javascript
function print() {
  console.log("Hello world.");
}
print(); // Hello world.
```


## 图片

### 普通图片

- 输入：`![背景图](/assets/images/bg.png)`
- 输出：![背景图](/assets/images/bg.png)

### 修改图片的样式

- 输入：

```
![背景图](/assets/images/bg.png){: style="width: 128px; height: 128px; object-fit: cover; float: right; animation: spin 10s linear infinite;" class="m-2 rounded-full" }

- 这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落。
```

- 输出：![背景图](/assets/images/bg.png){: style="width: 128px; height: 128px; object-fit: cover; float: right; animation: spin 10s linear infinite;" class="m-2 rounded-full" }

- 这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落这里有一段很长的段落。

> 不仅仅适用于图片，使用 `{: key="value" }` 的格式，可以在 Markdown 中为元素添加 HTML 属性。这里的示例甚至制作了动画效果。

## 数学公式

### 行内公式

- 输入：`$\Gamma(n) = (n-1)!\quad\forall n \in\mathbb N$`
- 输出：$\Gamma(n) = (n-1)!\quad\forall n \in\mathbb N$



### 块级公式

- 输入：

```
$$ ax^2 + bx + c = 0 \quad (a \neq 0)  $$

$$ x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$
```

- 输出：

$$ ax^2 + bx + c = 0 \quad (a \neq 0)  $$

$$ x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

> 使用鼠标右键生成的公式图片，还有小惊喜。


## 其他

### 文本倾斜

- 输入：`*文本倾斜*` / `_文本倾斜_`
- 输出：*文本倾斜* / _文本倾斜_

### 文本加粗

- 输入：`**文本加粗**` / `__文本加粗__`
- 输出：**文本加粗** / __文本加粗__

### 文本删除

- 输入：`~~删除线~~`
- 输出：~~删除线~~

### 分割线

- 输入：

```
*****
```

- 输出：

*****

> 单独一行，连续使用三个以上的 `-` 或 `*` 就可以生成分割线。
> 因为 `---` 会被识别为 `Front Matter`，所以推荐使用 `*` 号生成分割线。

### 链接

- 输入：`[Github](https://github.com)`
- 输出：[Github](https://github.com)

### 引用

- 输入：

```
> 通常用于引用一段其他地方的内容。
> 普通换行的内容，会接在上一行的结尾。
>
> 在引用中置空一行，才可以换行。
>
> > 引用的嵌套。
```


- 输出：

> 通常用于引用一段其他地方的内容。
> 普通换行的内容，会接在上一行的结尾。
>
> 在引用中置空一行，才可以换行。
>
> > 引用的嵌套。

### 脚注

- 输入：

```
- 第一句话有一个示例脚注一。[^footnote1]

[^footnote1]: 对脚注对象进行说明一。

- 第二句话有一个示例脚注二。[^footnote2]

[^footnote2]: 对脚注对象进行说明二。
```

- 输出：

- 第一句话有一个示例脚注一。[^footnote1]

[^footnote1]: 对脚注对象进行说明一。

- 第二句话有一个示例脚注二。[^footnote2]

[^footnote2]: 对脚注对象进行说明二。

### 键盘按钮

- 输入：`<kbd>Ctrl</kbd>/<kbd>Command</kbd> + <kbd>C</kbd>`
- 输出：<kbd>Ctrl</kbd>/<kbd>Command</kbd> + <kbd>C</kbd>

### Emoji

- 输入：<code class="language-plaintext">:<b></b>cat<b></b>: :<b></b>dog<b></b>:</code>

- 输出：:cat: :dog:

> 更多表情可以参考：[emoji-cheat-sheet](https://github.com/ikatyang/emoji-cheat-sheet)
