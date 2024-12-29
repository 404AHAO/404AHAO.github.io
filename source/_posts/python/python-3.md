---
title: python基础数据类型(一)
abbrlink: 338
date: 2023-03-12 04:09:08
tags: 
  - AHao
  - pyhton
categories: 学习笔记
cover: 'https://image.ahao.ah.cn/wallhaven-6dm5yw.png'
---

# 学习python的第三天

- 该文章主要学习内容：

- 布尔与空值
----------------------------------------------------------------------
## 数据类型介绍

> 数据类型

- 为什么有数据类型？(了解)

    - 更好分配管理内存

    - 方便统一管理

    - 更贴近人物分类管理习惯

> *数据类型种类(熟悉)*

<img src="https://image.ahao.ah.cn/ec4822d323d8f0981afc3097d4a876c.png"/>

- 数值类型是 `不可变` 类型。所谓的不可变类型，指的是类型的值一旦有不同了，那么它就是一个全新的对象。

- 数字1和2分别代表两个不同的对象，对变量重新赋值一个数字类型，会新建一个数字对象。

- 还是要强调一下 Python 的变量和数据类型的关系，变量`只是对某个对象的引用`或者说代号、名字、调用等等，变量本身`没有数据类型的概念` 。

- 只有1，[1，2]，"hello"这一类对象才具有数据类型的概念。

- *Python 支持三种不同的数值类型：整数、浮点数和复数与布尔。*

```
# int 不可变数据类型发生改变以后地址会变
a = 10
print(id(a))    #140726938792496
a = a + 2
print(id(a))    # 140726938792560

# list 可变数据类型发生改变以后地址不会变   
li = [1, 2, 3]  # li是一个列表
print(li)
print(id(li))   # 2453227786824
li.append(8)    # 把这个元素8添加到列表中 append()添加元素方法
print(li)
print(id(li))   # 2453227786824
```
> 整数(int)介绍(熟悉)

- 整数通常被称为整型，数值为正或者负，不带小数点。表示数字的时候，通常使用`十进制`(decimal) 来表示。

## 有时我们还会用八进制或十六进制来表示(了解)：

- 十六进制用0x前缀和0-9，a-f表示，例如：0xff00。python 中使用 `hex()` 将十进制转为十六进制

- 八进制用0o前缀和0-7表示，例如0o45。python 中使用 `oct()` 将十进制转为八进制

- 二进制用0b前缀和0-1表示，例如0b11。python 中使用 `bin()` 将十进制转为二进制

```
# 十进制-十六进制
print(hex(10))  # 0xa

# 十进制-八进制
print(oct(10))  # 0o12

# 十进制-二进制
print(bin(6))  # 0b110
```

> 整数内存(了解)

- *python*的整数长度为`32`位，并且通常是`连续分配内存空间`的。

- 从下面代码的内存地址看，之间正好相差32.

{% gallery %}
![](https://image.ahao.ah.cn/a0ad3c6854ffac85f602b93151d1d0c.png)
{% endgallery %}

> 小整数对象池(了解)

- pyhton 初始化的时候会自动建成一个`小整数对象池`，方便我们调用，避免后期重复生成！

- 这是包含262个指向整数对象的指针数组，范围是`-5到256`.

- 也就是说比如整数10，即使我们在程序里没有创建它，其实在python后台已经悄悄为我们创建了。
  
  - 作用：节约开销，增快运行速度

> 浮点数(float)介绍(熟悉)

- 浮点数也就是小数，如1.23，3.14，-9.01，等等。

- 但是对于很大或很小的浮点数，一般用科学计数法表示，把10用e代替，1.23x10^9就是1.23e9，或者12.3e8，0.000012可以写成1.2e-5，等等。

> 浮点数与整数之间转换(掌握)

<img src="https://image.ahao.ah.cn/Snipaste_2023-03-20_04-54-18.jpg"/>

```
a = 77.7
print((type(a)))    # <class 'float'>

# 整形-浮点型
b = 2
print(float(b))

# 浮点型-整形 不会四舍五入 直接把小数部分舍掉
c = 7.3
print(int(c))

# 复数
print(complex(2, 3))  # (2+3j)
```

> 数学计算(熟悉)

- 对于数学计算，除了前面提到过的简单的加减乘除等等，更多的科学计算需要导入 math 这个标准库，它包含了绝大多数我们可能需要的科学计算函数。

<img src="https://image.ahao.ah.cn/Snipaste_2023-03-20_05-07-10.jpg"/>

```
import math # 导入这个库,python内置
# ceil() 向上取整 不管小数位上的数(不包括0) 多小整数都会进一位 往大的数取
print(math.ceil(3.0))   # 3
print(math.ceil(3.1))   # 4
print(math.ceil(3.5))   # 4
print(math.ceil(3.9))   # 4
print(math.ceil(4.1))   #4

# floor() 向下取整 不管小数位上的数多大（不包括0） 全会舍掉 往小的数取
print(math.floor(7.0))  # 7
print(math.floor(7.1))  # 7
print(math.floor(7.5))  # 7
print(math.floor(7.9))  # 7
print(math.floor(0.9))  # 0

# pow(x, y) 求x的y次方 结果为浮点型
print(math.pow(2, 3))   # 8.8
print(2**3)

# sqrt() 开根号 >=0 结果为浮点型
print(math.sqrt(16))    # 4.0
# abs() 求绝对值
print(abs(-2))  # 2
print(abs(-90))  # 90

# round() 四舍六入 五成偶（整数部分是一个奇数会进一位，整数部分是偶数会舍掉）
print(round(3.4))   # 3
print(round(3.5))   # 4
print(round(3.7))   # 4
print(round(4.1))   # 4
print(round(4.5))   # 4
print(round(4.7))   # 5

a = 7.388
print(round(a, 2))  # 会四舍六入 7.39
```
# 布尔类型

> 布尔类型介绍

- 比如我们抛硬币，不是正面就是反面。

- 那其实对于对与错、0与1，都是传统意义上的布尔类型。
- 但在Python语言中，布尔类型只有两个值，True 与 False。
- 注意：首字母必须大写，不能有其它的花式变型。

> 布尔类型

- 我们通过python内置的`bool()`函数来测试一个表达式的布尔值的结果

![](https://image.ahao.ah.cn/1e055ba6fb42e948af1e59348992582.png)
![](https://image.ahao.ah.cn/73629ce9822f2fce401b9c242871c9b.png)

> bool()使用

- 归纳
  - 数值类型：0、0.0的 bool 值都为 False，其它的都为 True
  - 字符串：空字符串的 bool 值为 False，其它的都为 True。注意空格字符串为 True ![](https://image.ahao.ah.cn/a7cb86bf55632e93f638803bc8df4b9.png)
  - 列表：空列表的 bool 值为False，其它的都为 True。
  - None 的 bool 值永远为 False

> 布尔类型运算

布尔类型运算如下：
- and运算
- or运算
- not运算
- 算术运算。注意：把True看作1，而False看作0

# 空值
> 空值介绍
- 空值不是布尔类型，是 Python 里一个特殊的值，用` None `表示（首字母大写）。
`None `不能理解为0，因为0是整数类型，而` None `是`一个特殊的值`。None 也不是
布尔类型，而是 `NoneType`。
[](https://image.ahao.ah.cn/f374d635795fe290dcd4c0a5a281660.png)

> 思考：
以下分别输出10还是20？
- print(10 and 20)
- print(10 or 20)

  *短路(懒惰)原则*


```
布尔类型.py

if 10:
    print('hello')

# 数值类型布尔判断 除开0和0.0其他数值的布尔值都是为True
# print(bool(0))  # False
# print(bool(0.0))    # False
# print(bool(-3))   # True
# print(bool(8))  # True


# 字符串不二判断 只要不是非空的字符串
print(bool('hello'))    # hello
print(bool(''))    # False
print(bool(' '))    # True

print((3 > 2) > 1)  # True > 1  1>1
# 把True 看作1 把False 看作0
print(True + 1)
print(True + False)

print(True == 1)    # True
print(True == 3)    # False


# None 空值 不等于0
print(bool(None))   # False
print(type(None))   # <class 'NoneType'>

```


{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/wallhaven-6dm5yw.png)
{% endhideToggle %}


### 觉得该文章对您有帮助，可以在下方给博主留言(如有错误可以通过留言或者联系博主进行更改)
感谢您的观看，欢迎下次再见，再见
----------------------------------------------------------------------