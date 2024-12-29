---
title: 漫画下载器
categories: 资源分享
tags:
  - AHao
  - 漫画下载器
cover: 'https://image.ahao.ah.cn/wallhaven-ex2568.png'
abbrlink: '7147'
date: 2023-10-18 03:58:49
ai: true
---

# bilibili漫画下载器
今天给兄弟们分享一个漫画下载器黑科技`BiliBili Manga Dawnloader`，当然有跟作者商量过才分享出来


BiliBili Manga Dawnloader是一款目前`唯一一款开源并且好用的哔哩哔哩漫画下载器`，拥有ui图形界面(虽然简陋了点)，
而且支持关键词搜索漫画，黑科技下载未解锁章节
支持多线程下载，多种保存格式，本地漫画管理，
一键检查更新，非常的方便。
对于解锁黑科技下载未解锁章节，需要使用BiliPlus解析，项目有操作指引。

> 工具截图
![](https://image.ahao.ah.cn/85f979e140e791edd723fe3a108a58b.png)


# 工具使用指南
软件有两种下载解析方法

- B站解析
    - 只能下载免费章节和用户已解锁的章节
    - 首先获得你的Cookie
    - 方法一 
      - B漫手机客户端扫码登入
    - 方法二 
      - 手动获取Cookie:
    1. 以谷歌浏览器为例，打开B漫首页并且登入
    2. 点击 `F12` 打开开发者工具
    3. 点击 `应用` 标签
    4. 在边栏中找到 `Cookie` ，点击 `https://manga.bilibili.com`
    5. 在右侧的详情中找到 `SESSDATA`，复制 `值` 粘贴到程序设置选项中的 `我的Cookie` ，回车确认
    6. 如果提示 `Cookie有效`！ 那么就成功了！
    7. 否则请再次确认上述步骤，检查是否正确复制内容不含空格，还有疑问的话欢迎联系作者或提 `Issues`
- BiliPlus解析
    - 利用 biliplus 提供的 ComicWebReader 在线漫画平台的api来尝试获取未解锁的漫画章节
    - 该网站现有 4w+ 已关联 `Bilibili` 帐号的访客，也就是说很有概率你想看的漫画已经有人购买了，所以你可以白嫖
    - 特别提示: 毕竟是要提供 `Cookie` 给第三方网站托管，因此可能会有潜在的安全风险。敏感人群请不要使用自己主账号的 `Cookie`
    - `BiliPlus` 的 `Cookie` 获取方法跟上述一致，在 `ComicWebReader` 登入后在开发者工具中找到 `access_key` 粘贴到程序设置选项中的 `BiliPlus Cookie` 即可
  
# 下载地址
下载地址：[BiliBili-Manga-Downloader.7z](https://github.com/Zeal-L/BiliBili-Manga-Downloader/releases/download/v1.3.0/BiliBili-Manga-Downloader.7z)

国内用户加速通道：[BiliBili-Manga-Downloader.7z](https://cors.isteed.cc/github.com/Zeal-L/BiliBili-Manga-Downloader/releases/download/v1.3.0/BiliBili-Manga-Downloader.7z)

GitHub页面：https://github.com/Zeal-L/BiliBili-Manga-Downloader

# 群聊

如果你有好的`id`，或者其他技术分享可以扫下方的二维码添加群聊
![](https://image.ahao.ah.cn/cd6c67bffa1d94c40fca88560323d0e.jpg)
