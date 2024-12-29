---
title: hexo个人配置
tags:
  - AHao
  - Hexo
categories:
  - 必看内容
cover: 'https://image.ahao.ah.cn/romance-1465949.png'
ai: 
  - "这篇文章介绍了关于修改个人配置和主题的一些方法，包括修改主题下的文件、控制台日志配置以及水印标签的升级等内容。文章还介绍了hexo个人配置ANZHIYU主题的一些个人修改配置和主题的相关操作。例如，可以通过回退到上个版本再进行更新，或者参考安知鱼主题指南来修改配置。最后，文章还提供了一些常用的语法示例，如标题、段落、强调、列表、链接、引用和代码块等。"
  - "这篇文章介绍了hexo个人配置ANZHIYU主题的一些个人修改配置，包括配置主题下的文件修改和控制台打印日志配置。还介绍了即刻短文的水印标签升级更新主题的方法，并提到了如果喜欢博主的博客主题风格可以参考安知鱼主题指南。最后提到因为改了控制台打印的配置需要回退到上个版本再进行更新。文章中还提到了一些常用的语法，例如标题、段落、强调、列表、链接、图片、引用和代码块的使用方法。"
  - "这篇文章介绍了对hexo个人配置ANZHIYU主题进行个人修改配置的方法，包括文件的修改、控制台打印日志的配置、即刻短文的水印标签等。同时提到了主题的升级更新和回退版本的需要。文章还介绍了常用的语法，例如标题、段落、换行、强调、列表、链接、引用和代码块等。提供了示例和格式化的编写方法。"
abbrlink: '7795'
date: 2023-05-09 21:33:43
---

# ANZHIYU主题的一些个人修改配置

----------------------------------------------------------------------
> 配置1

- `anzhiyu主题` --> `layout` --> `includes` --> `anzhiyu` 下的 `log-js.pug` 文件

- 修改控制台打印日志


> 配置2

- `anzhiyu主题` --> `layout` --> `includes` --> `page` 下的 `album_detail.pug` 文件

- 修改即刻短文的水印标签


*升级更新主题*:在主题目录下，运行
```
git pull
```
或者删除theme/anzhiyu文件夹，然后重新安装即可。

方法来自安知鱼主题，如果喜欢博主的博客主题风格，可以参考

安知鱼主题指南：https://anzhiy.cn/docs/

由于我改了控制台打印的配置

所以需要回退到上个版本再进行pull更新

```
git reset --hard
git pull origin master
```
注：其中origin master表示git的主分支。

{% note success flat %}即刻短文aplayer音乐配置{% endnote %}

```
- content: 歌曲推荐
      date: 2023/05/12
      aplayer:
        server: tencent  # QQ音乐
        id: 003nie6G4YDE6a  # 通过参数referer获得
```
{% note success modern %}图片提示{% endnote %}
![](https://image.ahao.ah.cn/218b9b27914e3edbd9cde49e7b08af9.png)

{% note success flat %}标签配置{% endnote %}

1.`simple`样式
{% note simple %}默认 提示块标签{% endnote %}
{% note default simple %}default 提示块标签{% endnote %}
{% note primary simple %}primary 提示块标签{% endnote %}
{% note success simple %}success 提示块标签{% endnote %}
{% note info simple %}info 提示块标签{% endnote %}
{% note warning simple %}warning 提示块标签{% endnote %}
{% note danger simple %}danger 提示块标签{% endnote %}

```
{% note simple %}默认 提示块标签{% endnote %}
{% note default simple %}default 提示块标签{% endnote %}
{% note primary simple %}primary 提示块标签{% endnote %}
{% note success simple %}success 提示块标签{% endnote %}
{% note info simple %}info 提示块标签{% endnote %}
{% note warning simple %}warning 提示块标签{% endnote %}
{% note danger simple %}danger 提示块标签{% endnote %}
```

2.`modern`样式
{% note modern %}默认 提示块标签{% endnote %}
{% note default modern %}default 提示块标签{% endnote %}
{% note primary modern %}primary 提示块标签{% endnote %}
{% note success modern %}success 提示块标签{% endnote %}
{% note info modern %}info 提示块标签{% endnote %}
{% note warning modern %}warning 提示块标签{% endnote %}
{% note danger modern %}danger 提示块标签{% endnote %}

```
{% note modern %}默认 提示块标签{% endnote %}
{% note default modern %}default 提示块标签{% endnote %}
{% note primary modern %}primary 提示块标签{% endnote %}
{% note success modern %}success 提示块标签{% endnote %}
{% note info modern %}info 提示块标签{% endnote %}
{% note warning modern %}warning 提示块标签{% endnote %}
{% note danger modern %}danger 提示块标签{% endnote %}
```

3.`flat`样式
{% note flat %}默认 提示块标签{% endnote %}
{% note default flat %}default 提示块标签{% endnote %}
{% note primary flat %}primary 提示块标签{% endnote %}
{% note success flat %}success 提示块标签{% endnote %}
{% note info flat %}info 提示块标签{% endnote %}
{% note warning flat %}warning 提示块标签{% endnote %}
{% note danger flat %}danger 提示块标签{% endnote %}

```
{% note flat %}默认 提示块标签{% endnote %}
{% note default flat %}default 提示块标签{% endnote %}
{% note primary flat %}primary 提示块标签{% endnote %}
{% note success flat %}success 提示块标签{% endnote %}
{% note info flat %}info 提示块标签{% endnote %}
{% note warning flat %}warning 提示块标签{% endnote %}
{% note danger flat %}danger 提示块标签{% endnote %}
```

4.`disabled`样式
{% note disabled %}默认 提示块标签{% endnote %}
{% note default disabled %}default 提示块标签{% endnote %}
{% note primary disabled %}primary 提示块标签{% endnote %}
{% note success disabled %}success 提示块标签{% endnote %}
{% note info disabled %}info 提示块标签{% endnote %}
{% note warning disabled %}warning 提示块标签{% endnote %}
{% note danger disabled %}danger 提示块标签{% endnote %}

```
{% note disabled %}默认 提示块标签{% endnote %}
{% note default disabled %}default 提示块标签{% endnote %}
{% note primary disabled %}primary 提示块标签{% endnote %}
{% note success disabled %}success 提示块标签{% endnote %}
{% note info disabled %}info 提示块标签{% endnote %}
{% note warning disabled %}warning 提示块标签{% endnote %}
{% note danger disabled %}danger 提示块标签{% endnote %}
```

5.`no-icon`样式
{% note no-icon %}默认 提示块标签{% endnote %}
{% note default no-icon %}default 提示块标签{% endnote %}
{% note primary no-icon %}primary 提示块标签{% endnote %}
{% note success no-icon %}success 提示块标签{% endnote %}
{% note info no-icon %}info 提示块标签{% endnote %}
{% note warning no-icon %}warning 提示块标签{% endnote %}
{% note danger no-icon %}danger 提示块标签{% endnote %}

```
{% note no-icon %}默认 提示块标签{% endnote %}
{% note default no-icon %}default 提示块标签{% endnote %}
{% note primary no-icon %}primary 提示块标签{% endnote %}
{% note success no-icon %}success 提示块标签{% endnote %}
{% note info no-icon %}info 提示块标签{% endnote %}
{% note warning no-icon %}warning 提示块标签{% endnote %}
{% note danger no-icon %}danger 提示块标签{% endnote %}
```

以下是 Hexo Markdown 的常用语法：

1. 标题
使用 # 符号表示标题，# 的数量表示标题的级别，最多支持六级标题。例如：
```
# 一级标题
## 二级标题
### 三级标题
```

2. 段落和换行
Markdown 默认会忽略单个换行，如果需要换行，可以在行尾添加两个空格，或者使用空行分隔段落。

3. 强调
可以使用 * 或 _ 包裹文本来表示强调，单个 * 或 _ 表示斜体，两个 * 或 _ 表示加粗。例如：
```
*斜体文本*
_斜体文本_
**加粗文本**
__加粗文本__
```

4. 列表
有序列表使用数字加英文句点表示，无序列表使用减号、加号或星号表示。例如：
```
1. 有序列表项1
2. 有序列表项2
- 无序列表项1
- 无序列表项2
```

5. 链接
可以使用 [链接文本](链接地址) 的格式插入链接。例如：
```
[OpenAI官网](https://openai.com)
```

6. 图片
可以使用 ![替代文本](图片链接) 的格式插入图片。例如：
```
![示例图片](https://example.com/image.jpg)
```

7. 引用
可以使用 > 符号表示引用。例如：
```
> 这是一段引用的文本。
```

8. 代码块
可以使用三个反引号 ``` 包裹代码块，或使用四个空格缩进代码。例如：
```go
​```
console.log('Hello, World!');
​```
```

这些是 Hexo Markdown 的常用语法，你可以使用它们来编写格式化的文本内容。



<!--  https://image.ahao.ah.cn/172e82d37a9dbf5cc8c33089db128c7.jpg -->
<!-- https://image.ahao.ah.cn/b94e187f4dfc260fda871809c97c499.png -->
<!-- https://image.ahao.ah.cn/95b8715a475d0a4c19929dda9b7c29c.png -->
{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/romance-1465949.png)
{% endhideToggle %}

----------------------------------------------------------------------