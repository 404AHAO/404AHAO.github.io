---
title: 执行hexo d报错&&解决方案
tags:
  - AHao
  - Hexo
categories:
  - 必看内容
cover: 'https://image.ahao.ah.cn/20240112004559.jpg'
ai: true
abbrlink: bcf2
date: 2024-01-21 11:24:27
---

# 前言

原本一开始是没打算更新文章的，结果因为更新打赏列表上传的时候莫名其妙出现了一个`bug`
![](https://image.ahao.ah.cn/7877f15191006e191dba591ca832932.png)

根据以往的经验，我都是默认这种报错是哪篇文章的样式写错了，但想了一晚上好像上次更新也是一个多星期前了，

上一次更新到`hexo 7`版本之后好像也没出现什么问题，然后`噼里啪啦`得试了各种命令，结果还是没解决


# 查阅以及测试

没辙只能去`ChatGPT`问一下，得到的回复如下：
```
这个错误提示表明在尝试连接到github.com的443端口时发生了超时错误。这可能是由于以下几个原因导致的：

网络连接问题：首先，请确保您的网络连接正常。您可以尝试通过访问其他网站或使用其他网络连接来确认是否存在网络问题。如果是网络问题，您可以尝试重启您的网络设备，如路由器或调制解调器，或者联系您的网络服务提供商以获取更多支持。

防火墙或代理设置：如果您使用了防火墙或代理服务器，它们可能会阻止您与github.com建立连接。请检查您的防火墙或代理设置，并确保它们允许您访问github.com的443端口。您还可以尝试禁用防火墙或代理，然后再次尝试连接。

DNS问题：DNS（域名系统）解析可能会导致连接问题。您可以尝试使用其他DNS服务器，如Google Public DNS（8.8.8.8）或Cloudflare DNS（1.1.1.1），来解析github.com的IP地址。您可以在操作系统或网络设置中更改DNS服务器设置。

SSL证书问题：如果您在连接到github.com时遇到SSL证书错误，可能是由于证书过期、无效或不受信任所致。请确保您的操作系统和浏览器是最新的，并且具有最新的根证书。您还可以尝试清除浏览器缓存和证书缓存，然后再次尝试连接。

如果您尝试了上述步骤仍然无法解决问题，建议您联系您的网络管理员或您的互联网服务提供商以获取更多支持和调试。

```
看回复好像本地和github的链接已经失效了，也可能是太久没用gitbash了

1. 首先，重新生成了本地电脑和`Github`链接的`SSH`的公钥`KEY`，将本地电脑和`GitHub`重新进行链接

```
git config --global user.name "your github user name"

git config --global user.email "your github 注册邮箱"
```

上述代码执行后，会重新生成以下格式的`公钥`

```
ssh-****** -t rsa -C "your github 注册邮箱"
```

此时公钥保存在`C:\Users\xxx\.ssh` 的文件夹下，打开`id_rsa.pub`文件，将里面的内容全部复制； 然后去`GitHub`的`Settings`, 找到`SSH and GPG keys`的页面,新建一个`SSH Key`, 将刚才复制的内容粘贴到新建的`SSH Key`中并点击保存。

> ps:不过我测试了一下好像并不是这个原因，毕竟`GitHub`的密钥并没有变化，但这样做肯定有它的道理

# 解决方案

1. 异常

在重新链接`github`时，执行`ssh -T git@github.com` 命令时，出现上图的情况，也就是：
```
ssh: connect to host github.com port 22: Connection timed out
```

2. 解决方法

在上方生成的文件夹：`C:\Users\xxx\.ssh`下，也就是存放公钥私钥(`id_rsa`和`id_rsa.pub`)的文件里，新建一个`txt`文本然后改成`config`文件，将下方内容复制到`config`文件里面：

```
Host github.com
User YourEmail@163.com
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
```

其中User为登录github的账号名称。
再次执行`ssh -T git@github.com`时，会出现提示如下，回车`yes`即可。
![](https://image.ahao.ah.cn/b135a8b86a0183e52b4036bf58833a1.png)

这时验证就可以通过。
![](https://image.ahao.ah.cn/527e59b569ea9a59c894fe0d19c6d53.png)

这样就解决了执行`hexo d`报错的问题啦~