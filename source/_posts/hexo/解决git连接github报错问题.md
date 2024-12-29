---
title: 解决git连接github报错问题
abbrlink: 22bb
date: 2024-01-26 04:59:20
tags:
  - AHao
  - Hexo
categories:
  - 必看内容
cover: 'https://image.ahao.ah.cn/20240112004053.jpg'
ai: true
---

# 缘由

果然太久没写文章就是容易出问题，这篇文章其实是跟上一篇文章：
{% link 执行hexo d报错&&解决方案,博客文章,https://cloud.ahao.ah.cn/posts/bcf2.html,https://image.ahao.ah.cn/20240112004559.jpg %}
同时遇到的

起因是因为太久没更新主题版本，想着顺便更新一下 `AnZhiYu`主题的版本，结果出现了报错：`Failed to connect to github.com port 443: Timed out`

原本以为是因为用了`dev`版本的缘故，所以出现`bug`了，后面开了`魔法`发现还是无法更新版本，甚至连`稳定的版本`都下载不下来

# 解决方法

1. 查看是否能正常打开`github`

{% link GitHub官网链接,全球最大的同性交流网站,https://github.com/ %}

因为我开了`魔法`，所以查看的时候是可以的，说明没问题

2. 最后上百度查了相关问题的解决方法

- 有魔法：就继续挂魔法，然后使用下方命令(选其一即可)
命令格式：
```git
git config --global http.proxy http://127.0.0.1:7890

git config --global https.proxy http://127.0.0.1:7890

```

- 没有魔法：就试着清理魔法缓存(选其一即可)
命令如下:
```git
git config --global --unset http.proxy

git config --global --unset https.proxy

```

3. 如果以上两个命令都没用的话，就试下最后一个，忽略 `SSL` 的验证

```git
git config --global http.sslVerify false

```

# 最后

如果上面的方法都没法解决的话，就只能下载 `GitHub`的客户端了，相关方法博主已经放到了

{% link 百度官网,支持在线查看的百科全书(虽然大部分都是广告),https://baidu.com/,https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png %}

中供各位翻看查阅了
