---
title: python中的变量与输入输出
abbrlink: 28902
date: 2023-03-06 04:50:52
tags: 
  - AHao
  - pyhton
cover: 'https://image.ahao.ah.cn/wallhaven-yx57dd.jpg'
categories: 学习笔记
post_copyright: false
---

# 学习python的第一天

- 该文章主要学习内容：

- 变量与输入输出


---------------------------------------------------------------------------------------------------------
# 标识符

所谓的标识符就是对变量、常量、函数、类等对象起的名字。

首先必须注意的是，Python语言在任何场景都严格区分大小写！也就是说A和a代表的意义完全不同

```
>>>a = 1
>>>A
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'A' is not defined
```
python对于表示标识符的命名有如下规定：

1. *第一个字符必须是字符表中的字符或者下划线*

例如，a，abc，_id，等都是可以的。但是例如$a(以$开头的是PHP的变量语法)，~abc，123a都是不可以的。这一点一定要注意。

可能有人会问，中文可以作为标识符嘛？答案是可以的，但是不建议大家这样做。

```
>>>姓名 = "小明"，打印出‘’ 结果是json
>>>姓名
'json'
```

另外，以下划线开头的标识符通常都有特殊意义。以单下划线开头的变量，例如_foo代表禁止外部访问的类成员，需通过类提供的接口进行访问，不能用"from xxx import *"导入。而以双下划线开头的，例如`__foo`，代表类的私有成员 以双下划线开头和结尾的`__foo__`是python里特殊方法专用的标识。如`__init__`代表类的构造函数。这些我们后面会专门的讨论这里不做过多的解释。

2. *识符的其他的部分由字母、数字和下划线组成（首字符不可以是数字）*

标识符除了**首字符不可以是数字外**，其他部分还可以包含数字。这里需要注意特殊字符是不可以的。例如：

a123b，bbc，a_b_c_1这些都是可以的。但是a&b，a-b-c这些都是不可以的。

另外要注意的是，由于l(小写的L)和数字1， 大小写的o与数字0在外观上的相似性，请尽量不要让它们相邻出现，保持语义的清晰性，确保不会发现错误认读的情况。

同样，英文中夹塞中文在语法上也是可以的，但绝对不要这么做！

```
>>>a这都能行b就服你 = 100
>>>a这都能行b就服你
100
```

3. *标识符对大小写敏感*

刚刚上面也给大家说过了，标识符ab和AB是完全不同的两个标识符

4. *变量名全部小写，常量名全部大写*

这条不能算语法层面的要求，而是代码规范的要求。
 可以用PI来表示一个变量，但通常我们都会认为这是代表圆周率的一个常量

5. *函数和方法名用小写加下划线*

这算是一个代码的规范，我们在定义一个方法的时候。尽量用get_images，count_apple之类的命名方式。当然也可以采用小驼峰的方式，getImages，countApple这种。

6. *类名用大驼峰*

同样也是代码规范，例如ThreadMinxIn，ButtonClick这种。就是每个单词的首字母大写，组合在一起就像是驼峰一样高低排列。

7. *模块和包的名字用小写*

请尽量小写模块和包的名字，并且不要和标准库以及著名的第三方库同名。如果同名程序运行会报错。

最后提醒大家，变量的命名`不要用关键字和内置函数`的名称！！

*python保留字*

Python`保留字`，也叫`关键字`，是Python语言官方确定的用作语法功能的专用标识符，不能把它们用作任何自定义标识符名称。关键字只包含小写字母。可以通过python提供的库输出这些关键字

<img src="https://image.ahao.ah.cn/9187426d741ce5c4da0ccec7ea85557.png"/>

Python的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字

```
>>>import keyword
>>>keyword.kwlist
```
如果真的用关键字来当做变量，会怎么样呢？

```
>>>if = 1
  File "<stdin>", line 1
    if = 1
       ^
SyntaxError: invalid syntax
```
系统会直接提示语法错误，所以这里一定要注意不要用关键字来当做变量。除了不能使用关键字作为标识符，内置的函数同样也是不可以的。sum是一个求和的函数。这里我给它定义成一个字符串看看会有什么结果？

```
>>>sum([1,2,3])    # 求和函数
6
>>>sum = 1
>>>sum([1,2,3])    # 报错TypeError-->失去原有的功能
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'int' object is not callable
```

> *python数据类型*

**数据类型**

- int类型：整数 十进制的数

- float类型：浮点数 带小数的数

- bool：布尔类型 True(真)或False(假) 

- str类型：字符串,以成对单引号或双引号包裹 成对出现 不能一单一双

~~注意：我们可以通过type() 函数输出数据类型~~


{% hideBlock 点击查看相关代码 %}  
```
变量.py

# int 整形 十进制
# str 字符串 被单引号或者双引号包裹 成对出现 不能一单一双
# float 浮点型 带小点的数
# bool 布尔类型 True False 真 假 首字母大写
# print('hello')

print("hello")  # 程序员入门必敲的第一行代码

print(type(6))  # <class 'int'>

print(type(6.6))  # <class 'float>

print(type('hello'))  # <class 'str‘）

print(type(True))  # <class 'bool'>
```
{% endhideBlock %}

> *变量*

**变量的定义**

变量是`容器`

变量是在`创建时`都会`在内存中开辟一块空间，用于保存它的值`

> **变量的创建**

变量创建小贴士：

- 在python当中创建变量`无需声明类型`

- 每个变量在`使用前都必须赋值`，变量`赋值以后才会被创建`

- “=”号这个赋值运算符是`从右往左`的计算顺序

- python允许`同时为多个变量赋值`

{% hideBlock 点击查看相关代码 %}  
```
变量.py

# 变量（盒子）就是一个装东西的
name = 'ho'  # 将ho赋值给name

a = 10  # a变量里面存的就是10
print(a) # 打印a输出里面的值

b = c = d = 5
print(b)
print(c)
print(d) # 结果都为5

age = 'hello'
```
{% endhideBlock %}
> **命名规制**

- 大小写敏感(敏感肌了属于是)

- 只能以 字母 数字 下划线 组成(数字不能开头)

- 见名知意

- 蛇形| 小驼峰| 大驼峰 命名法

- 不以关键词作为标识符

{% hideBlock 点击查看相关代码 %}  
```
变量命名.py

# 区分大小写
NAME = '(岁岁)'
name = '平安'
print(NAME)

# 只能以数字字母下划线组成 不能以数字开头
age2 = 20
print(age2)
_gender = '女'
print(_gender)

# 3t=student = '小明‘ # 不能以数字开头
# print(3student) # 运行会报错

# 见名知意
age = 18
neme = '小爱'
sex = '女'
weight = 170

# 蛇形 穿插在一起大写
StudentageS = '一高一低'
# 小驼峰  打一个单词首字母小写
studentEmail = 1600759690
# 大驼峰 第一个单词首字母大写
logicEdu = '阿豪の博客'
```
{% endhideBlock %}

> python标识符

**python关键字**

***['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await',***
***'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except',***
***'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda',***
***'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']***

{% hideBlock 点击查看相关代码 %}  
```
python关键字.py

# 不能以关键字（保留字）命名
# if = 0
# print(if)

# 查看python关键字(35个)
import keyword # 导入内置模块
print(keyword.kwlist) # 输出打印关键字
#['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await',
# 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except',
# 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda',
# 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```
{% endhideBlock %}

**变量的创建**

当执行 name = '张三'，python解释器做了什么呢？

1. 在内存中创建了一个 "张三"的字符串对象；

2. 在内存中创建了一个名为 name 的变量，并把它指向 '张三'

<img src="https://image.ahao.ah.cn/f702e203e08c0046ef0cb50ec44e297.jpg"/>

> *输入与输出*

**input输入函数**

- input() 是内置函数，用来`获取用户输入`，`返回值`为`字符串`。

-当用户未输入时，程序会停止向下执行，等待用户输入

撕烤：

- <img src="https://image.ahao.ah.cn/ed881f9e341d104d6da10ea99cf6a1d.jpg"/>

阻塞状态：

- <img src="https://image.ahao.ah.cn/680c9245364ef6049c0a64c8502b434.jpg"/>

{% hideBlock 点击查看相关代码 %}  
```
输入输出函数.py

# input() 输入函数 我们自己（用户）从键盘上输入得一个值 接受数据类型为str字符串
name = input('我只是一个提示，会原样输出：')
print(name)  # ‘18’
print(type(name))  # <class 'str'>
print("hello")
```
{% endhideBlock %}

> input输入函数小练习

- 输入年龄

- 当年龄大于18，则输出"你好呀，叼毛"；

- 否则输出"你好呀！小朋友"

- str.isdigit(): 判断字符串是否全部为数字组成

{% hideBlock 点击查看代码 %}  
```
输入输出函数.py

age = input('请输入你的年龄：')
# # if 条件判断：
# #   代码块
# # else:
# #   代码块
# # '12'--12  12 >=18
# # 强转 int()
if int(age) >= 18:  # 12>18?不成立
    print('你好呀小靓仔！')
else:  # if条件不满足直接执行else
    print('你好呀小朋友！')

```
{% endhideBlock %}

> **输入与输出**

- print() 输出函数

- print() 方法用于`打印输出`，最常用的一个函数

- 语法： print(self, *args, sep=''. end='\n', file=None)

{% hideBlock 点击查看相关代码 %}  
```
输入输出函数.py

# print() 输出函数 把我们想要输出的打印到控制台
# 可以用光标对准print()函数键盘上按CTRL点击进入查看
# end 在最后一个字符串后面添加一个指定的符号 默认换行
print('hello', end='*')  # 等价于print('hello',end='\n')
print('hello')
# sep 在两个值中间插入一个指定的符号，默认空格
print(4, 5, 4, 5, 6, sep='*')  # 4*5 print(4,5)

# 字符串相加 连接操作
print('4'+'5')   # 45

# sex = '女'
```
{% endhideBlock %}

> 小栗子

1. 打印输出-->小宇的年龄：18

2. 打印输出-->小宇的年龄时18，性别为女性

{% hideBlock 点击查看代码 %}        
```
age = 18
sex = '女性'
print('小宇的年龄是：', age, sep='')
print('小宇的年龄是：', age, ',性别为', sex, sep='')
```
{% endhideBlock %}

常用参数：

- sep：分隔符符号，在值之间插入的字符串，默认为空格

- end：字符串追加在最后一个值之后，默认为换行符\n。

- 如果，设置end='',则可以不换行，让print在一行内连续打印。


```
text.py

# int 不能直接和str进行比较
print('17' > '18')
# str和str比较是ASCII码
```

> 简单的收银超市代码案例

{% hideBlock 点击查看相关代码 %}  
```
# 引号里面是什么输出来就是什么
# 加了引号就是一个字符串 str
# 整数 1，2，3，4，5，6， int
# print('hello') 输出函数
# 带小数点的数都是浮点型 float
# input() 输入函数 用户从键盘输入 默认输入数据类型是一个str
# 乘法 *号
print('Logic超市收银系统')
name = input('商品名称： ')
price = input('商品价格： ')
count = input('商品数量： ')
discount = input('商品折扣： ')

# 应收=商品价格*商品数量*商品折扣
# 强转 '2'--2 字符串2--整形2  str--int
yingshou = float(price)*int(count)*float(discount)
print('应收：', yingshou)

# 实收：用户给的钱
print ('-'*30)
print ('logic超市--购物小票')
print('名称', '价格', '数量', '折扣')
print(name, ' ', price, ' ', count, ' ', discount)

print('-'*15)
# 找零= 实收-应收
print('应收', yingshou)
shishou = float(input('实收：'))
print('实收', shishou)
lingqian = shishou-yingshou
print('找零', lingqian)
```
{% endhideBlock %}

> 简单的藏头诗代码案例

{% hideBlock 点击查看相关代码 %}  
```
# 切片
# 下标从0开始
# str作加法是拼接 str*整数 乘以多少字符串就重复几次 str不能作除法和减法
word1 = input('请输入你的诗句：')
word2 = input('请输入你的诗句：')
word3 = input('请输入你的诗句：')
word4 = input('请输入你的诗句：')
print(word1[0],word2[0],word3[0],word4[0])
print(word1[0] + word2[0] + word3[0] + word4[0])
```
{% endhideBlock %}

~~博主使用的python版本为3.6版本~~

{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/wallhaven-yx57dd.jpg)
{% endhideToggle %}

### 觉得该文章对您有帮助，可以在下方给博主留言(如有错误可以通过留言或者联系博主进行更改)
感谢您的观看，欢迎下次再见，再见
---------------------------------------------------------------------------------------------------------
