---
title: python数据类型(二)
date: 2023-03-20 05:29:03
tags: 
  - AHao
  - pyhton
categories: 学习笔记
cover: 'https://image.ahao.ah.cn/animes-girl-1425819-wallhere.com.png'
abbrlink: 11782

---

# 学习python的第四天

- 该文章主要学习内容：

- 字符串
----------------------------------------------------------------------
# 字符串(str)

> 字符串介绍

- 字符串是 Python 中最常用的数据类型之一，使用`单引号`或`双引号`来创建字符串，使用`三引号`创建多行字符串

注意：
- 字符串的单引号与双引号都是`成对`出现的，不能一边单一边双。
- 字符串是`不可变`的`序列数据类型`，不能直接修改字符串本身，和数字类型一样！

> 字符串的存储

思考： 以下`数值`与`字符串`存储是一样的吗？
<img src="https://image.ahao.ah.cn/7ae17df6b27e7be5013c4b67a468fd5.png"/>

整数在内存中占一个字节，字符串不管中间多少内容都要单独存储。
<img src="https://image.ahao.ah.cn/026be8d1c0ea8da3526a2952a69b1fb.png"/>

> 字符串的下标

由于字符串是`序列数据结构`，所以我们可以通过`下标`将字符串中某个字母取出下标也可以称为`索引`。默认`从0开始`。

思考：
name = "hello world",如何取出e值？如何取出最后一个值？
<img src="https://image.ahao.ah.cn/5c34b371ad5ef2ac31f82e9ec4ba066.png"/>

> 字符串的切片

<img src="https://image.ahao.ah.cn/5bc5b179f4f3e0558f161ed1517e5cd.png"/>

撕烤：
name = "hello world",如何取出 world，hlowrd值？ name逆序输出？

<img src="https://image.ahao.ah.cn/928c63ada8f3dc42ea8e86b854c7b57.png"/>

注意：
- 索引默认从0开始
- 切片时左闭右开
- 当取单个字符的时候，索引超出范围会报错。而切片时不会报错。
- 步长不能为0，也不允许为浮点数

```
字符串介绍.py

# str 字符串是不可变的
s = 'qahbdhh236778'
# 三引号创建的字符串会保留原样格式
s1 = """
print('hello')
你好哦
你吃饭了嘛
"""
# print(s1)
#
# print('a' in 'abc')
# print(7 and 789)

# print('abbb jjj')



home = 'family'
name = 'hello world'
# 取'e' 找到对应的下标 字符串名字[值对应的下标]
# print(name[1])  # e
# print(name[10])  # d
# print(name[-1])  # y
# print(name[1])  # d
# 取单个值超出索引范围
# print(name[20]) # IndexError: string index out of range
# print(name[1.0]) 报错

# 切片
# [开始的位置默认为0：结束位置默认为-1：步长默认为1][左闭右开）
# 步长为正数是从前往后取，如果是负数就是从后往前，步长不能为0也不能为浮点型
name = 'hello world'
# 取到hello
# print(name[0:5])    # 拿的是索引为0-4的值
# 取hlowrd
# print(name[0:11:2])
# 取多个值超出索引范围不会报错 会输出源字符串
# print(name[1:30])   # ello world

# hello world- dlrow olleh
# print(name[::1])    # hello world
# print(name[::-1])   # dlrow olleh

# 取全部
# print(name[::1])
# print(name[:1])

home = 'family hel'
# f  a  m  i  l  y     h  e  l
# 0  1  2  3  4  5  6  7  8  9
#                     -3  -2  -1
# leh
print(home[2:7:-1])  # 2-7是从前往后，步长-1是从后往前，矛盾了，取不到
print(home[-1:-4:-1])   # leh
print(home[2:5:1])  # mil
print(home[5:2:-1])  # yli
print(home[5:2:1])  # 冲突了 矛盾
print('hello')

```


> 字符串类型转换
<img src="https://image.ahao.ah.cn/2e353ebcf20eecfa91f83d9028e2c5c.png"/>

```
str int互转.py

# str - int
# int只能转换纯数字的字符串
a = '1234'
a1 = int(a)
print(type(a1))   # <class 'int'>

# int - str
# 浮点型可以转换str
b = 123.5
b1 = str(b)
print(type(b1))    # <class 'str'>
```

> 字符串组成方式
- 字符相加
- 字符串格式化
  - `%s %d %f`
  - `str.format()`
  - python3.6.4 引入`f''`

栗子:
- name = 'hansen'
- age = 20
- 输出**的年龄为**

```
字符串特殊操作.py

# s = 'hello'
# e = 'china'
# print(s+e)  # 字符串相加并做拼接
#
# print(s*2)  # 乘以几次就重复几次

# 字符串不能做除法和减法

name = 'hansen'
age = 20
# 输出xx的年龄为xx岁
# print('hansen的年龄为20岁')

# 第一张 %s：字符串str %d : 整形int  %f：浮点型float
print(name, '的年龄为：', age, sep='')   # 常规写法
print('%s的年龄为%d' % (name, age))
print('{}的年龄为{}'.format(name, age))
print(f'{name}的年龄为{age}岁')
```

> 字符串常见操作

- S.find(sub) --> 返回该元素最小的索引
- S.index(sub) --> 返回该元素最小的索引
- S.replace(old, new[, count]) --> 替换
- S.split(sep=None) --> 以sep来分割字符串,并返回列表。sep默认为None,分割默认为空格
- S.startswith(prefix[, start[, end]]) --> 判断字符串是否以前缀开始，返回为bool值。
- S.endswith(suffix[, start[, end]]) --> 判断字符串是否以尾缀结束，返回为bool值。
- S.lower() --> 将字符串全部转为小写
- S.upper() --> 将字符串全部转为大写
- S.strip([chars]) --> 默认去掉字符串左右的空格
- S.isalpha() --> 判断字符串是否全为字母，返回的是bool值
- S.isdigit() --> 判断字符串是否全为数字，返回的是bool值
- S.isalnum() --> 判断字符串是否全为数字或者字母，不存在特殊字符，返回的是bool值
- S.join(iterable) --> 将序列中的元素以指定的字符连接生成一个新的字符串

```
字符串内置方法.py

# # find() 返回元素对应的最小下标 当查找的元素不存在时返回-1
# s = 'hello'
# print(s.find('l'))
# print(s.find('a'))
#
# # index() 返回元素对应的最小下标 查找的元素不存在时会报错
# print(s.index('l'))
# print(s.index('a'))  # ValueError: substring not found

# s1 = 'i am a girl girl'
# replace(old,new,count) count 替换次数
# girl-boy
# replace 在做操作之前会先把原字符串先复制一份，然后是在复制的字符串上面进行操作，所以原字符串不会改变
# s1 = s1.replace('girl', 'boy')
# print(s1.replace('girl', 'boy'))
# print(s1)

# split() 以指定的字符分割字符串 默认是空格 结果以列表呈现
# s2 = 'i am a girl'
# # print(s2.split())
# print(s2.split('a'))
#
# s3 = 'h-h-aa-a-ah-'
# print(s3.split('-'))

# startswith 判断是否以什么开头 （T F)
# s4 = '#i am a boy'
# print(s4.startswith('#！'))
#
# # endswith 判断是否以什么结尾
# print(s4.endswith('boy'))
#
# # lower() 转小写 没有参数
# s5 = 'TBBfff'
# print(s5.lower())   # tbbfff
#
# # upper() 转大写
# print(s5.upper())   # TBBFFF

# strip() 默认去除字符串前后的空格 删除前后指定的字符 ， 如果是中间的不会报错会输出原字符串
# s6 = '￥china@'
# print(s6.strip('na@'))
# print(s6.strip('c'))

# join() 以指定的字符连接生成新的字符串
s = 'hello'
a = ' '.join(s)
print('-'.join(s))
print(type(a))  # <class 'str'>

print('*'.join(s))

s6 = '345hggf&*'
print(s6.isdigit())  # 判断字符串是否全部由数字组成，返回结果是布尔类型
print(s6.isalpha())  # 判断字符串是否全部由字母组成
print(s6.isalnum())  # 判断字符串是否全部由字母数字组成，不包含特殊符号

```

{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/animes-girl-1425819-wallhere.com.png)
{% endhideToggle %}



### 觉得该文章对您有帮助，可以在下方给博主留言(如有错误可以通过留言或者联系博主进行更改)
感谢您的观看，欢迎下次再见，再见
----------------------------------------------------------------------
