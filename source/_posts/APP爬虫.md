---
title: APP爬虫
password: zwy
abstract: '有东西被加密了, 请输入密码查看.'
message: '您好, 这里需要密码.'
theme: xray
wrong_pass_message: '抱歉, 这个密码看着不太对, 请再试试.'
wrong_hash_message: '抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.'
abbrlink: '2914'
date: 2023-11-22 05:20:16
tags:
---

# 前言
此文章是因为之前有部分逻辑教育的学员缺失了后面最后两节课的内容，所以我抽空以笔记的方式进行补齐

> 以下为正文内容

# APP爬虫
## 介绍
爬虫分类：数据来源
- PC端爬虫(网页端爬虫)
  - 找数据接口(requests,scrapy)
  - selenium
- APP端爬虫
  - 找数据接口 (支付宝(网页端没有任何数据)  抖音)
    - 如何找数据接口 -`fiddler`
    - 如何获取app与服务器进行交互的数据包-`模拟器`
  - appium(类似于网页端的selenium)



app爬虫常见反爬
1. 抓不动数据包请求
2. 抓去数据包里的参数设计加密(app逆向`并未包含在课程当中，可以上B站大学查看相关内容`)

APP抓包常用工具:
![](https://image.ahao.ah.cn/5a1a8ad121ca7d00bd1c3f2c359a83f.png)

# 模拟器

在电脑端模拟手机的运行场景或程序操作
常见模拟器：
- 雷电模拟器
- 夜神模拟器(课程推荐，比较好用，不会太容易被封禁)
> 夜神模拟器网址：
{% link 网址链接, 夜神模拟器,https://www.yeshen.com/ %}


# 安装APP




