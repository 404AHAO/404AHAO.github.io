---
title: python数据类型(三)
tags:
  - AHao
  - pyhton
categories: 学习笔记
cover: 'https://image.ahao.ah.cn/325390659cf55c01dcbaf83bf225-1467771.png'
abbrlink: 7ff8
date: 2023-04-15 04:59:42
---

# 学习python的第五天

- 该文章主要学习内容：

- 列表、元组、字典、集合
----------------------------------------------------------------------
# 列表(list)

> 列表介绍

- 列表时python中最基本也是最常用的数据结构之一,它是一个`有序可重复的元素集合`。
- 从数据结构角度看。python的列表时一个`可变长度`的顺序存储结构，每一个位置存放的都是对象的指针。

- 我们可对列表进行 修改、切片、追加、删除、嵌套、迭代、成员判断 等操作。

> 列表创建
- 创建一个列表，只要把`逗号`分割的`不同的数据元素`使用`方括号`括起来即可。
![](https://image.ahao.ah.cn/3b1020bb21aa4e345b7d4b1b410f33c.png) 

- 除此之外，我们还可以直接通过`lisk()`来进行创建列表
![](https://image.ahao.ah.cn/1c0480067e9374bf2a96f3a272e1bfe.png)

- 注意：
  - 变量名最好不适用`list`
  - 列表里的`元素`可以是`任意类型`
  - `iterable`表示`可迭代的对象`，简单来说就是可以一个一个元素取出来的。比如：str

```
列表创建访问.py

# list 可变 可以存放不同类型可重复元素的集合
# 创建1
li = [1, 2.4, 'hello', 'hello', True, [1, 2]]
print(li)
print(type(li))    # <class 'list'>
li1 = []    # 空列表
print(type(li1))

# 创建二
# list(iterable) iterable 可迭代对象-str-list -可以把元素一个一个取出来
li2 = list('abduiooi4')
print(li2)

```

> 访问(查)列表内的元素
- 列表 `从0开始` 为它的每一个元素顺序创建 `下标索引`，直到 `总长度减一` 。要访问它的某个元素，以方括号加下标值的方式即可。

- 注意要确保索引不越界，一旦访问的 `索引超过范围`，会抛出异常。所以，一定要
记得最后一个元素的索引是 len(list)-1。

- 思考：
- li = [1, 2]是 如何取出元素的呢？

![](https://image.ahao.ah.cn/8d87a8ef4224a7d6a4f6a6b37762978.png)

```
列表创建访问.py

# 访问
li3 = [3, 6, 9, 10]
# 9
print(li3[2])   # 9
# print(li3[10])  # IndexError: list index out of range 索引超出会报错

```

> 修改列表内的元素

- 直接`取出元素`进行`重新赋值`

- 思考：
- li = ["a", "b", "c"] 是怎么把"a"改为"A"的呢？
![](https://image.ahao.ah.cn/a021a5439c49d77a51fc6102ca3c6fa.png)

```
列表创建访问.py

s = 'abv'
s1 = '123'
# 'a'-'A'
print(s[0], type(s1[0]))
s[0] = 'A'   # 报错 不能修改
print(s)

#  修改
li4 = [25, 7, 10, 30]
# 25-52
li4[0] = 52    # 找到对应的下标 直接赋值
print(li4)
```

- 直接`取出元素`，再通过`del语句`或者`list.remove()`或者`list.pop()`进行删除
![](https://image.ahao.ah.cn/cf5d55c3a2ec7d4102c84c58f05a3d1.png)

```
列表元素增删.py

li = ['小明', '小红', '小刚', '小爱']
# 添加
# 李明
# append() 把元素添加到列表末尾
li.append('李明')
li.append([1, 2, 3])    # 可以在列表里嵌套列表
print(li)

# 小白 放到公司的最前面
# insert(下标，值) 指定位置插入
li.insert(0, '小白')    # 如果指定位置超出 会放到最后面
print(li)

# 啊玲 啊斌 啊鑫 --一起办入职
# extdnd(iterable) 将一个序列中的多个值追加到列表里
li1 = ['啊玲', '啊斌', '啊鑫']
li.extend(li1)
print(li)

# 删除
li = ['小明', '小红', '小刚', '小爱', '小峰']
# del 通过下标去删除值
# 删除第0个人
del li[0]
print(li)
# 删除整个列表
del li
print(li)   # 不复存在 家没了 公司倒闭

# 辞退小峰
# remove() 通过值去删除
li.remove('小峰')
li.remove('峰')  # ValueError: list.remove(x): x not in list 删除的值不存在时会报错
print(li)

# pop() 默认删除最后一个元素
li.pop()
li.pop(1)   # 传入的参数是下标 通过下标去删除
print(li)

```

> 列表的特殊操作

![](https://image.ahao.ah.cn/34925b829eb90462603ab463b641c51.png)

```
列表特殊操作内置函数.py

# 列表相加 拼接
li = [1, 2, 3]
li1 = [2, 3, 4]
print(li + li1)  # [1, 2, 3, 2, 3, 4]

# 列表相乘 乘以几就出现几次
print(li * 2)  # [1, 2, 3, 1, 2, 3]

print(4 in li1)

```

> 常用内置函数
![](https://image.ahao.ah.cn/1d8009a80449051b2ff9c543f6ebf1a.png)

```
列表特殊操作内置函数.py

li = [1, 2, 3, [3, 4]]
# 取4
print(li[3][1])

# len()求序列的长度
s = 'hello'
print(len(s))  # 5

li5 = [2, 3, [3, 5]]
print(len(li5))  # 3

# max() 求最大值
li6 = [1, 2, 3, 90]
print(max(li6))
li7 = ['v', 'ac', 'er']
print(max(li7))

li8 = ['3', 90, 'abc']
# print(max(li8)) # 列表中有int，str一起存在时会报错

# min()
li9 = [8, 7, 9]
print(min(li9))
```

> 列表的排序与反转
![](https://image.ahao.ah.cn/e9094898730e7c703a06b5e571dfa1b.png)

```
列表的排序与反转.py

li = [1, 3, 4, 6]
print(li[::-1])
li.reverse()
print(li)

li1 = [5, 4, 7, 25, 24]
# 升序 小-大
li1.sort(reverse=True)  # 默认升序 reverse=False  降序reverse=True
print(li1)

```

> 列表的切片
![](https://image.ahao.ah.cn/f1b27bedabf0d03728f86cc656a34fc.png)

- 思考：
- li = [1,2,3,4,5,6,7]取[2,3,4]以及取出[2,4,6]

```
列表的排序与反转.py

# 切片[起始位置：结果位置：步长]
li = [1, 2, [3, 78], 3, 4, 5, 6, 7]
# [2,3,4]
# print(li[1:4])
#
# # 取[2,4,6]
# print(li[1::2])
#
# # 取[1,3,5]
# print(li[:6:2])

# 取78
print(li[2])    # li[2]=[3, 78]
print(li[2][1])
```

> 列表常见操作
- L.append(object) --> 在列表末尾添加新的对象
- L.extend(iterable) --> 用新列表扩展原来的列表
- L.count(object) --> 统计某个元素在列表中出现的次数
- L.index(value) --> 从列表中找出某个值第一个匹配项的索引位置
- L.insert(index, object)--> 将对象插入列表
- L.pop([index]) --> 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值
- L.remove(value) --> 移除列表中某个值的第一个匹配项
- L.reverse() --> 反向列表中元素
- L.sort(reverse=False) --> 对原列表进行排序
- L.copy() --> 复制列表
- L.clear() --> 清空列表

```
列表常见函数.py

# count 计数 返回元素出现的次数
li = [4, 5, 6, 8, 5, [5, 5]]
print(li.count(5))  # 2

# index() 返回下标
print(li.index(5))
print(li.index(100))    # ValueError: 100 is not in list


# copy() 复制列表
li3 = [1, 2, 3]
li4 = li3.copy()    # 重新开辟了一个空间去存储他，改变复制的列表的时候原列表不会变
print(li4)
li4.append(8)
print(li3)

# clear() 只会清空元素 列表还在 家还在
li5 = ['岁岁', '平安']
li5.clear()
print(li5)  # []

```

# 元组(tuple)

> 元组介绍
- 元组也是 `序列结构`，但是是一种 `不可变序列`，你可以简单的理解为内容不可变的列表。除了在内部元素不可修改的区别外，元组和列表的用法差不多。

> 元组创建
- 创建一个元组，只要把 `逗号` 分隔的 `不同的数据元素` 使用 `小括号` 括起来即可。

![](https://image.ahao.ah.cn/74561b7a537010b5e5e6045f15e6f61.png)

- 除此之外，我们还可以直接通过 `tuple()` 来进行创建元组。
![](https://image.ahao.ah.cn/bd5976b3c85c59d9e40d0b598496534.png)

> 元组与列表相同的操作
- 使用 `方括号加下标` 访问元素
- `切片`（形成新元组对象）
- `tuple.count()` | `tuple.index()`
- python内置函数：`reversed()`，`sorted()`
- 加法及乘法


```
元组.py

# 为什么有了列表还要有元组?
# tuple 不可变
# 创建1
t = (1, 2, 35, 6)
print(type(t))
t1 = (1,)   # 如果元组只有一个数据，要在后面加一个逗号
print(type(t1))
tu3 = ()
print(tu3)
print(type(tu3))

# 创建2
# tuple(iterable)
t3 = tuple([2, 'hello', 8, 10])
print(t3)

# 访问 通过下标访问
print(t3[1])

# 切片
a = (2, 3, 4, 5, 6, 7)
print(a[1:5])   # (3, 4, 5, 6)

# count 返回元素出现的次数

# index 返回最靠前的索引

a = (2, 3, 4, 5, 6, 7)
# a[0] = 10  # 报错 不能修改
print(a)

a = (2, 3, ['小零', 20])
# a = (2, 3, ['小零', 20])  # 报错
# 20-18
a[2][1] = 18
print(a)

# 元组相加
t1 = (1, 2, 3)
t2 = (5, 6, 7)
print(t1 + t2)

# 元组相撑
print(t1 * 2)   # (1, 2, 3, 1, 2, 3)

# list - tuple
l = [1, 2, 3]
t = tuple(l)
print(t)

# tuplr - list
tt = (1, 2, 3)
l2 = list(tt)
print(l2)



tu = (23, 24, 8, 9)
print(tuple(reversed(tu)))  # <reversed object at 0x000002125F7AAE08> 返回的是一个对象 需要查看结果需强转

print(tuple(sorted(tu, reverse=True)))   # 默认升序 返回结果是list


# sort 是永久改变
li = [23, 6, 8]
li.sort(reverse=True)
print(li)   # 排序的结果 [23, 6, 8]
print(li)   # 排序以后的结果 [23, 6, 8]

# sorted() 临时改变
li = [23, 6, 8]
print(sorted(li))   # 排序的结果 [6, 8, 23]
print(li)   # 排序以后的结果 [23, 6, 8]

'''
数据不需要修改用元组
需要修改用列表
元组消耗内存比列表要小
元组安全性更高，数据不容易被更改
'''

```

> 元组中不允许的操作
- `不`允许 `修改` 、`新增` 元素。(一级)
- `不`允许 `删除` 某个元素（但可以删除整个元组）

**实际上，元组没有任何会对内部元素发生 `修改` 动作的方法。例如，元组没有remove，append，pop 等方法**

> 元组与列表之间的转换
![](https://image.ahao.ah.cn/e698348fc79dcdcbfdf48d5a176b014.png)


# 字典(dict)
> 字典介绍
- Python 的字典数据类型是基于 hash 散列算法实现的，采用 `键值对(key:value)` 的形式，根据 key 的值计算 value 的地址，具有非常快的查取和插入速度。它是一种 `可变对象` ，所以支持修改、插入、删除等操作。

> 字典创建
![](https://image.ahao.ah.cn/ce4724a9ae626ca2beb92633f406e59.png)

注意：
- 在 Python3.6 开始，字典对象会保持键值插入时的 `顺序`，并且其包含的 `元素个数不限`，`值的类型` 也可以是其它`任何数据类型`。
- 字典的 `key` 必须是 `不可变的对象`，例如整数、字符串、bytes 和元组，但使用最多的还是字符串。 列表、字典、集合等就不可以作为 key。同时，同一个字典内的 `key 必须是唯一` 的，但值则不必。

![](https://image.ahao.ah.cn/3872102702f72563ace6d1184d287de.png)

```
字典.py

# 字典 dict 可变
# 创建一
# 字典名 = {键:值，键:值 }
d = {'name': '岁岁', 'age': 20}
print(type(d))  # <class 'dict'>
print(d)

# 创建二
# 字典名= dict(键=值， 键=值， 键= 值)
dic1 = dict(name='小丁', age=20)
# dic2 = dict(12 = 'hello', age = 30)
# 如果键是int类型，用第一种方法
dic = {12: 20, 29: 20}
print(dic1)

# 键必须是不可变的 int str tuple 值没有要求
d1 = {(1, 2, 3): 20, 'a': 12}
d1 = {[1, 2, 3]: 20, 'a': 12}   # 报错 list可变的
print(d1)

# 当字典中有两个一样的键 默认会保存后面一个键值对
d2 = {'age': 20, 'age': 25}
print(d2)
print(len(d1))

# print(d2[0])    # 不能通过下标取值
```

> 访问字典

- 字典是 `集合类型`，不是序列类型，因此 `没有索引下标` 的概念，更 `没有切片` 的说法。但是，与 list 类似，字典采用把 `相应的键` 放入 `方括号` 内获取 `对应值` 的
方式取值。

如：`dic[exit_key]`

思考：当 key 值不存在时，程序会怎么样呢？
<img src="https://image.ahao.ah.cn/739e36d3ee412d1d493bef217b9b254.png"/>

```
字典.py

# 访问
dic = {'name': '岁岁', 'age': 20}
print(dic['name'])  # 通过键获取值
print(dic['tel'])   # 当查找的键不存在是会报错

print(dic.get('tel'))   # None 键不存在返回None
```

> 字典的增加与修改
- `增加` 就是往字典 `插入新的键值对`
- `修改` 就是给 `原有的键赋予新的值`。由于一个 key 只能对应一个值，所以，多次对一个 key 赋值，后面的值会把前面的值 `覆盖` 掉。

```
字典.py

# 增加
dic1 = {'name': '岁岁'}
print(dic1)
li = ['age', 20]
dic1[li[0]] = li[1]
# 字典名[键]=值
# 键值对不存在就新增，存在就覆盖
dic1['gender'] = '女'
print(dic1)  # {'name': '岁岁', 'age': 20, 'gender': '女'}
# 如果给一个键多次赋值 ， 只会保留最后一对
dic1['gender'] = '男'
print(dic1)
```

> 一系列删除
- 删除字典元素：`del dic[exit_key] 或 dic.pop(exit_key)`
- 删除整个字典：`del dic`
- 清空整个字典：`dic.clear()`

```
字典.py

# 删除
# del 字典名[键]
del dic1['name']    # 键删掉后值也会被删掉
print(dic1)
del dic1
print(dic1) # 不复存在 家没了 报错
dic1 = {'name': '岁岁', 'age': 20}
dic1.pop('name')    # 要传参 传的是键
print(dic1)

dic1.clear()    # 只会删除元素 家还在 是个空字典
print(dic1)  # {}
```

> 字典常见操作
- D.items() --> 以列表返回可遍历的(键, 值) 元组对
- D.keys() --> 以列表返回字典所有的键
- D.values() --> 以列表返回字典所有的值

```
字典.py

# 内置访问
dic1 = {'name': '岁岁', 'age': 20, 'addr': '广东'}
print(dic1.keys())  # dict_keys(['name', 'age', 'addr']) 返回字典里所有的键
print(dic1.values())    # dict_values(['岁岁', 20, '广东']) 返回字典里所有的值
print(dic1.items())  # 反正字典所有键值对

for i in dic1.values():
    print(i)
```

# 集合(set)
> 集合介绍

- 集合( set )是一个 `无序不重复` 元素的集，基本功能包括关系测试和消除重复元素。是 `可变数据类型`。
- 集合数据类型的 `核心` 在于 `自动去重`。

> 集合创建

- 集合使用 `大括号 {}` 框定元素，并以 `逗号` 进行分隔。

- `s = {ele1,ele2,ele3...}`
- `s = set()`
- `s = set(iterable)`

注意：
  - `{}` 并 `不是` 创建 `空集合`，而 `是空字典`。创建 `空集合` 需使用 `set()`

```
集合.py

# 可变 list dict set
# 不可变 int str tuple
# 集合 set 可变
# 自动去重且无序
s = {1, 2, 3, 4, 3, 3, 5}   # 初始化时必须要包含值，否则会被认为是集合类型
s1 = set()  # 用这种方法才能创建一个空集合
print(type(s))
print(type(s1))  # <class 'set'>
print(s)

# 可迭代对象 str list tuple 通过下标去取值
s3 = set('hello')
s4 = set((1, 2, 35, 2, 2, 45, 100))
s5 = set([3, 3, 3, 3, 45])
print(s3)
print(s4)
print(s5)
```

> 添加元素
- 通过 `set.add(key)` 方法可以 `添加元素` 到 set 中

注意：
- 可以重复添加，但是会 `自动去重`，所以无效果
- `不能添加可变对象`

```
集合.py

# 添加
s3 = {2, 3, 4, 5}
s3.add('h')
s3.add('h')  # 可以重复添加 但是会自动去重 无意义
s3.add([1, 2, 3])   # TypeError: unhashable type: 'list' 不能添加可变对象
s3.add((1, 2, 3))   #作为一个整体
print(s3)

```

> 集合更新
- 可以通过 `set.update()` 方法，将另一个对象 `更新` 到 `已有的集合中`，这一过程同样会进行 `去重`。

```
集合.py

# update(可迭代对象)
s3.update([1, 2, 3])
s3.update((1, 2, 3))
s3.update({'name': 'suisui'})   # 添加字典的话只会保留键
print(s3)
```

> 删除元素

- `set.remove(key)`：删除指定元素
- `set.pop()`：随机删除元素(注意：无参数)

注意：
  - `集合不能取出某个元素`，因为集合既不支持下标索引也不支持字典那样的通过键值对获取。

```
集合.py

# 删除
s3 = set('hello')
print(s3)
s3.remove(4)    # 根据值删除
print(s3)
s3.remove(90)   # 删除的值不存在会报错
s3.discard(90)  # 删除的值不存在会报错
print(s3)
s3.pop()    # 没有参数
print(s3)
```

{% hideToggle 封面图片 %}
<img src="https://image.ahao.ah.cn/325390659cf55c01dcbaf83bf225-1467771.png"/>
{% endhideToggle %}




### 觉得该文章对您有帮助，可以在下方给博主留言(如有错误可以通过留言或者联系博主进行更改)
感谢您的观看，欢迎下次再见，再见
----------------------------------------------------------------------