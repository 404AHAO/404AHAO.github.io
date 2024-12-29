---
title: 利用PicGo搭建个人图床(白嫖又拍云版)
tags: 
  - AHao
  - 图床
cover: 'https://image.ahao.ah.cn/wallhaven-j3m8y5.png'
categories:
  - 必看内容
# path: 编程
abbrlink: 56846
date: 2023-03-09 02:35:15
ai: true
---

## 注意：

- 该文章需要有自己的域名为前提

- 注意：此文章只针对Windows版本`其他版本我也不会`

- 部分引用文章：https://sanshui.vip/2022/11/07/1/

*官方文档：*

- 链接：https://www.kancloud.cn/easyimage/easyimage/3121105

- github地址:https://github.com/icret/EasyImages2.0

---------------------------------------------------------------------------------------------------------

## PicGo目前支持以下图床:

- 腾讯云cos

- 阿里云oss

- SM.MS

- GitHub

- 七牛云

- Imgur

- 又拍云

## 特点

- 支持API
- 支持仅登录后上传
- 支持设置图片质量
- 支持压缩图片大小
- 支持文字/图片水印
- 支持设置图片指定宽/高
- 支持上传图片转换为指定格式
- 支持限制最低宽度/高度上传
- 支持上传其他文件格式
- 在线管理图片
- 支持网站统计
- 支持设置广告
- 支持图片鉴黄
- 支持自定义代码
- 支持上传IP黑白名单
- 支持上传日志IP定位
- 支持限制日上传次数
- 支持创建仅上传用户
- 对于安装环境要求极低
- 对于服务器性能要求极低
- 理论上支持所有常见格式
- 更多功能支持请安装尝试···

## 下载地址
- 点击即可跳转 [GitHub](https://github.com/Molunerfinn/PicGo/releases/download/v2.3.1/PicGo-Setup-2.3.1-x64.exe) | [Gitee](https://gitee.com/icret/EasyImages2.0/repository/archive/master.zip) | [稳定版](https://github.com/icret/EasyImages2.0/releases) 上传至web目录

- 也可以通过链接：https://github.com/Molunerfinn/PicGo/releases/tag/v2.3.1 

- 在详情页最下方点击箭头所指位置进行下载：

- <img src="https://image.ahao.ah.cn/29a64d1087be045182d4aff85b31c99.png"/>


> 安装示范：

*PS：`由于博主已经安装过了，下面的内容只是为了示范`*

*下载完成后双击应用开始进行安装*

<img src="https://image.ahao.ah.cn/d8f098c3dfcd0293ec178fa67426787.png"/>

*可以根据自己的实际应用，一般都是`仅为我安装即可`, 直接点击下一步*
<img src="https://image.ahao.ah.cn/d0e6740369a97afcea0985c12d38ce0.png"/>

*选择自己想要存放的安装路径,`博主是直接放在F盘根目录下`，确定好后直接点击安装*

<img src="https://image.ahao.ah.cn/45a44149f97f32ee1cfff5b5dfae969.png"/>

*安装完成后点击启动即可*


> 又拍云

### *1.先注册账号并且进行实名认证*

- 进入页面后点击总览

<img src="https://image.ahao.ah.cn/9e202e6145930fd41700ded85ddecef.png"/>

### *2.点击云存储，并且点击立即使用*

<img src="https://image.ahao.ah.cn/b8351a85412af42ce799a62c9068172.png"/>

### *3.在服务管理这里点击创建服务*

<img src="https://image.ahao.ah.cn/55d0a88c8a316b374fa837af49029a1.png"/>

### *4.服务名称可以随便写一个，然后选择应用场景为`网页图片`*

<img src="https://image.ahao.ah.cn/015c91ecdbcd675fe9b769dd15aaa92.png"/>

### *5.点击新建管理员,并勾选`可读取、可写入、可删除`*

<img src="https://image.ahao.ah.cn/bd37f275f9a9327f199950de446afda.png"/>

### *6.将操作员账号和密码保存下来,一会需要在PicGo图床上配置需要用到!(一定要记住)*

- 创建后会弹出服务创建成功并分配测试域名

### *7.创建成功后进击进入配置*

<img src="https://image.ahao.ah.cn/5a5dd1d70e759047bcd91460d519f17.png"/>

### *8.添加绑定域名*

<img src="https://image.ahao.ah.cn/0c2d6371f0afb54db070b9cd83978e1.png"/>

### *9.域名输入后会生成解析记录值(复制到你购买所域名的运营商进行解析，博主用的是`华为云`)*

<img src="https://image.ahao.ah.cn/fa909b35bb3a429031d3d0e5980542e.png"/>

### *10.解析的内容一定要一一对应(`值`需要用双引号进行包裹)*

<img src="https://image.ahao.ah.cn/cd04b28aa6bea433054f6c12cc8ca28.png"/>

### *11.完成之后回到又拍云点击添加即可*

- 最后再将CNAME解析一下就完成了(方法同上)

<img src="https://image.ahao.ah.cn/4e90a633d12c881b9b4810dfeecb62d.png"/>


*审核成功后右上角小铃铛处会有消息提醒,此时你的云储存服务就已经创建成功了,接下来开始配置图床.*

### *12.将图床域名(证书)配置为HTTPS*

- 没有也无所谓，依旧可以白嫖

    - 点击云产品

    - SSL证书，点击申购证书

<img src="https://image.ahao.ah.cn/5a608a8860568333c1cdc7dd9b2b511.png"/>

*SSL证书申购*

<img src="https://image.ahao.ah.cn/20d848e07cb4d7f1bb7b6795ebe49b0.png"/>

- 点击创建订单(立省1900元 `每日省钱小妙招`)

- 一般等10分钟左右就通过审核了(也有可能要一天，看地区)

<img src="https://image.ahao.ah.cn/7053700f536dd2ed13b311a9366ab78.png"/>

**回到云储存**

- 功能配置 
    - HTTPS
    
    - HTTPS设置，将白嫖来的证书粘贴进去就好了


> PiGo配置

*需要填写的内容*

**设定Bucket**

<img src="https://image.ahao.ah.cn/957899cf1a59f8093377adaf982aeb4.png"/>

- 也就是在又拍云最开始创建的服务名称

**操作员跟密码**

- 设定操作员,也就是我们第5小点要你记住的操作员跟密码(如果实在忘记了也没关系)

- 点击储存管理滑倒最下方有个操作员授权，重新生成即可

<img src="https://image.ahao.ah.cn/64519630f0665233ad1a0dd204c832c.png"/>

**加速域名**

- 回到域名管理复制你绑定的域名

<img src="https://image.ahao.ah.cn/f9a8a7076a31a015135f8593412dfc3.png"/>

*完整设置*
<img src="https://image.ahao.ah.cn/0a52a0da53d87218541d5fbb540caf5.png"/>

- 完成这些后可以设置为默认图床，点击确定就完成配置了

*如何使用*

- 将格式链接设置为`url`，将图片`拖拽`进去就可以了

<img src="https://image.ahao.ah.cn/6329909fbcd18bc23eda5625ead54c2.png"/>

- 上传成功后可以点击相册查看已经上传的图片(上传成功后链接会自动复制)

<img src="https://image.ahao.ah.cn/82446fdbf4b3ea4d905086c915e293a.png"/>

*此时你的图床就搭建好了,PicGo图床有很多实用的功能,你可以在设置里自行更改,官方提供了大量扩展插件,可以按照自己需求来安装。[插件](https://link.zhihu.com/?target=https%3A//github.com/PicGo/Awesome-PicGo)*

> 又拍云图床后台

链接：https://link.zhihu.com/?target=https%3A//github.com/PicGo/Awesome-PicGo

~~*以上为搭建图床的所有内容*~~


{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/wallhaven-j3m8y5.png)
{% endhideToggle %}


### 觉得该文章对您有帮助，可以在下方给博主留言(如有错误可以通过留言或者联系博主进行更改)
感谢您的观看，欢迎下次再见，再见
---------------------------------------------------------------------------------------------------------
