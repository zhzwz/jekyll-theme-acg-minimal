---
title: Rendering effect of Markdown syntax
description: Introduce the Jekyll Theme ACG theme's support and usage of Markdown syntax.
categories: ["Jekyll Theme ACG"]
tags: ["markdown", "english"]
math: true
lang: en-US
---

> My English is poor. In the event of any discrepancy, the Simplified Chinese post shall prevail.

## Introduction

 John Gruber and Aaron Swartz created Markdown in 2004 as a markup language that is appealing to human readers in its source code form.[9]

> Markdown is a lightweight markup language for creating formatted text using a plain-text editor.
>
> Markdown is widely used in blogging, instant messaging, online forums, collaborative software, documentation pages, and readme files.
>
> —— [Wikipedia](https://en.wikipedia.org/wiki/Markdown)
> {: class="text-right" }

The Markdown syntax standard supported by Github is called [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown), or GFM for short. Jekyll Theme ACG supports some other features besides GFM syntax.


## List

### Unordered list

- Input:

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

- Output:

- A
  - a
    - i
    - ii
  - b
    - I
    - II
- B

### Ordered list

- Input:

```
1. A
   1. a
   1. b
   1. c
2. B
3. C
```

- Output:

1. A
   1. a
   1. b
   1. c
2. B
3. C

> Unordered numbers will automatically become ordered.

### To do list

- Input:

```
- [x] TODO 1
- [ ] TODO 2
- [x] TODO 3
- [ ] TODO 4
```

- Output:
- [x] TODO 1
- [ ] TODO 2
- [x] TODO 3
- [ ] TODO 4


## Table

### Standard table

- Input:

<pre><code class="language-markdown"># Examples of tables in standard Markdown syntax
| Column A | Column B | Column C |
| :------- | :<span>------</span>: | -------: |
|   Left   |  Center  |  Right   |
|    A     |    B     |    C     |
</code></pre>

- Output:

| Column A | Column B | Column C |
| :------- | :------: | -------: |
|   Left   |  Center  |  Right   |
|    A     |    B     |    C     |

### Ignore headers and alignment

Unlike standard Markdown syntax, the header and alignment of the table can be omitted.

- Input:

```
| 1 | 2 | 3 |
| 4 | 5 | 6 |
| 7 | 8 | 9 |
```

- Output:

| 1 | 2 | 3 |
| 4 | 5 | 6 |
| 7 | 8 | 9 |

### Custom alignment

- Input:

<pre><code class="language-markdown"># Each cell can use `:` to control its own alignment.
| ########## | ########## | ########## |
|:   Left    |:  Center  :|   Right   :|
|:  Center  :|   Right   :|:   Left    |
|   Right   :|:   Left    |:  Center  :|
</code></pre>


- Output:

| ########## | ########## | ########## |
|:   Left    |:  Center  :|   Right   :|
|:  Center  :|   Right   :|:   Left    |
|   Right   :|:   Left    |:  Center  :|

### Combine table columns

- Input:

<pre><code class="language-markdown"># The cells between `||` will be merged.
| 1 | 2 | 3 |
|: 45 :|<b></b>| 6 |
|: 789   :|<b></b>|<b></b>|
</code></pre>

- Output:

| 1 | 2 | 3 |
|: 45 :|| 6 |
|: 789   :|||

### Combine table rows

- Input:

<pre><code class="language-markdown"># The cells beginning with `^^` will be merged.
| 1 | 2 |  3  |
| 4  5 |<b></b>|^^ 6 |
|^^ 7 8|<b></b>|  9  |
</code></pre>

- Output:

| 1 | 2 |  3  |
| 4  5 ||^^ 6 |
|^^ 7 8||  9  |


## Code

### Single line of code

- Input: ``` `const name = "jekyll-theme-acg";` ```

- Output: `const name = "jekyll-theme-acg";`

### Multiple lines of code

- Input:

<pre><code class="language-markdown">```javascript
function print() {
  console.log("Hello world.");
}
print(); // Hello world.
```</code></pre>

- Output:

```javascript
function print() {
  console.log("Hello world.");
}
print(); // Hello world.
```


## Picture

### Normal picture

- Input: `![picture](https://cdn.jsdelivr.net/gh/coderzhaoziwei/jekyll-theme-acg/assets/images/pixiv86925095.png)`
- Output: ![picture](https://cdn.jsdelivr.net/gh/coderzhaoziwei/jekyll-theme-acg/assets/images/pixiv86925095.png)

### Modify the style of the picture

- Input:

```
![picture](https://cdn.jsdelivr.net/gh/coderzhaoziwei/jekyll-theme-acg/assets/images/pixiv86925095.png){: style="width: 128px; height: 128px; object-fit: cover; float: right; animation: spin 10s linear infinite;" class="m-2 rounded-full" }

- There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here.
```

- Output: ![picture](https://cdn.jsdelivr.net/gh/coderzhaoziwei/jekyll-theme-acg/assets/images/pixiv86925095.png){: style="width: 128px; height: 128px; object-fit: cover; float: right; animation: spin 10s linear infinite;" class="m-2 rounded-full" }

- There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here. There is a very long paragraph here.

> Not only for images, but with the format of `{: key="value" }`, you can add HTML attributes to elements in Markdown. The examples here even produced animation effects.

## Mathematical formula

### In-line formula

- Input: `$\Gamma(n) = (n-1)!\quad\forall n \in\mathbb N$`
- Output: $\Gamma(n) = (n-1)!\quad\forall n \in\mathbb N$


### Block-level formula

- Input:

```
$$ ax^2 + bx + c = 0 \quad (a \neq 0)  $$

$$ x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$
```

- Output:

$$ ax^2 + bx + c = 0 \quad (a \neq 0)  $$

$$ x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$


## Others

### Slanted text

- Input: `*Slanted text*` / `_Slanted text_`
- Output: *Slanted text* / _Slanted text_

### Bold text

- Input: `**Bold text**` / `__Bold text__`
- Output: **Bold text** / __Bold text__

### Deleted text

- Input: `~~Deleted text~~`
- Output: ~~Deleted text~~

### Dividing line

- Input:

```
*****
```

- Output:

*****

> On a single line, use more than three `-` or `*` in a row to generate dividing lines.
> it is recommended to use `*` to generate dividing lines, because `---` will be recognized as `Front Matter`.

### Link

- Input: `[Github](https://github.com)`
- Output: [Github](https://github.com)

### Quote

- Input:

```
> Usually used to quote a piece of content elsewhere.
> The content of ordinary line breaks will be attached to the end of the previous line.
>
> Leave a blank line in the quote to wrap the line.
>
> > Nesting of references.
```


- Output:

> Usually used to quote a piece of content elsewhere.
> The content of ordinary line breaks will be attached to the end of the previous line.
>
> Leave a blank line in the quote to wrap the line.
>
> > Nesting of references.

### Footnote

- Input:

```
- The first sentence has an example footnote one. [^footnote1]

[^footnote1]: Explain the object of footnote one.

- The second sentence has an example footnote two. [^footnote2]

[^footnote2]: Explain the object of footnote two.
```

- Output:

- The first sentence has an example footnote one. [^footnote1]

[^footnote1]: Explain the object of footnote one.

- The second sentence has an example footnote two. [^footnote2]

[^footnote2]: Explain the object of footnote two.

### Keyboard buttons

- Input: `<kbd>Ctrl</kbd> / <kbd>Command</kbd> + <kbd>C</kbd>`
- Output: <kbd>Ctrl</kbd> / <kbd>Command</kbd> + <kbd>C</kbd>

### Emoji

- Input: <code class="language-plaintext">:<b></b>cat<b></b>: :<b></b>dog<b></b>:</code>

- Output: :cat: :dog:

> More emoji: [emoji-cheat-sheet](https://github.com/ikatyang/emoji-cheat-sheet)
