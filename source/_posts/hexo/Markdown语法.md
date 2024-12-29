---
title: Markdown语法
tags:
  - AHao
  - Hexo
cover: 'https://image.ahao.ah.cn/anime-1562445.jpg'
abbrlink: '5878'
date: 2023-05-22 01:07:06
---

Hexo是一款流行的静态博客生成器，支持Markdown语法。在Hexo中，Markdown语法可以让你轻松地创建博客文章，包括标题、段落、列表、代码块、链接等等。本文将详细介绍Hexo Markdown的所有语法。

----------------------------------------------------
1. 标题

在Hexo中，你可以使用#号来表示标题。#号的数量表示标题的级别，最多支持6级标题。例如：
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
2. 段落

在Hexo中，你可以使用空行来表示段落。例如：
```
这是第一段。

这是第二段。
```
3. 列表

在Hexo中，你可以使用*或-来表示无序列表，使用数字和.来表示有序列表。例如：
```
* 无序列表1
* 无序列表2
* 无序列表3

1. 有序列表1
2. 有序列表2
3. 有序列表3
```

4. 引用

在Hexo中，你可以使用>来表示引用。例如：
```
> 这是一段引用。
```
5. 代码块

在Hexo中，你可以使用```来表示代码块。例如：

```go
console.log('Hello World!');
```


6. 链接

在Hexo中，你可以使用[]()来表示链接。[]内是链接名称，()内是链接地址。例如：
```
[Hexo官网](https://hexo.io/)
```

7. 图片

在Hexo中，你可以使用![]()来表示图片。[]内是图片名称，()内是图片地址。例如：
```
![Hexo Logo](https://hexo.io/logo.png)
```

8. 粗体和斜体

在Hexo中，你可以使用**表示粗体，*表示斜体。例如：

```
**这是一段粗体文字。**

*这是一段斜体文字。*
```

9. 分栏 Tabs

{% tabs 标签语法 %}

<!-- tab 标签语法 -->

```Markdown
{% tabs Unique name, [index] %}

<!-- tab [Tab caption] [@icon] -->

Any content (support inline tags too).

<!-- endtab -->

{% endtabs %}
```

<!-- endtab -->

<!-- tab  配置参数 -->

1. Unique name :
   - 选项卡块标签的唯一名称，不带逗号。
   - 将在#id 中用作每个标签及其索引号的前缀。
   - 如果名称中包含空格，则对于生成#id，所有空格将由破折号代替。
   - 仅当前帖子/页面的 URL 必须是唯一的！
2. [index]:
   - 活动选项卡的索引号。
   - 如果未指定，将选择第一个标签（1）。
   - 如果 index 为-1，则不会选择任何选项卡。
   - 可选参数。
3. [Tab caption]:
   - 当前选项卡的标题。
   - 如果未指定标题，则带有制表符索引后缀的唯一名称将用作制表符的标题。
   - 如果未指定标题，但指定了图标，则标题将为空。
   - 可选参数。
4. [@icon]: - FontAwesome 图标名称（全名，看起来像“ fas fa-font”） - 可以指定带空格或不带空格； - 例如'Tab caption @icon' 和 'Tab caption@icon'. - 可选参数。

<!-- endtab -->

<!-- tab 示例代码 -->

> Demo 1 - 预设选择第一个【默认】

```Markdown
{% tabs test1 %}

<!-- tab -->

**This is Tab 1.**

<!-- endtab -->

<!-- tab -->

**This is Tab 2.**

<!-- endtab -->

<!-- tab -->

**This is Tab 3.**

<!-- endtab -->

{% endtabs %}
```

> Demo 2 - 预设选择 tabs

```Markdown
{% tabs test2, 3 %}

<!-- tab -->

**This is Tab 1.**

<!-- endtab -->

<!-- tab -->

**This is Tab 2.**

<!-- endtab -->

<!-- tab -->

**This is Tab 3.**

<!-- endtab -->

{% endtabs %}

```
> Demo 3 - 没有预设值

```Markdown
{% tabs test3, -1 %}

<!-- tab -->

**This is Tab 1.**

<!-- endtab -->

<!-- tab -->

**This is Tab 2.**

<!-- endtab -->

<!-- tab -->

**This is Tab 3.**

<!-- endtab -->

{% endtabs %}

```

> Demo 4 - 自定义 Tab 名 + 只有 icon + icon 和 Tab 名

```Markdown
{% tabs test4 %}

<!-- tab 第一个Tab -->

**tab 名字为第一个 Tab**

<!-- endtab -->

<!-- tab @fab fa-apple-pay -->

**只有图标 没有 Tab 名字**

<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->

**名字+icon**

<!-- endtab -->

{% endtabs %}

```

<!-- endtab -->

{% endtabs %}


以上就是Hexo Markdown的所有语法，希望对你有所帮助。如果你想了解更多关于Hexo的内容，请访问Hexo官网。