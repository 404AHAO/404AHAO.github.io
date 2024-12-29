---
title: 如何快速更新anconda
tags:
  - AHao
  - anconda
categories:
  - 必看内容
cover: 'https://image.ahao.ah.cn/09551233ad4cd71ad280182d515a793.jpg'
ai: true
abbrlink: c9fb
date: 2023-05-10 07:50:12
---

# Anconda更新

- 让你不再因为conda更新太慢而烦恼
----------------------------------------------------------------------
# 起因

其实写这篇文章纯粹是想记录一下五一期间为了把python3.6版本升级到3.8，然后更新anconda更新太久这件事，

根据网上能查到的更新anconda的方法基本都是通过换源的方式进行安装

也就是通过命令 `conda config --set show_channel_urls yes` 生成 `.condarc `这个文件

通过修改生成的`.condarc`文件，添加以下内容：

```
channels:
  - defaults
show_channel_urls: true
default_channels:
  - http://mirrors.aliyun.com/anaconda/pkgs/main
  - http://mirrors.aliyun.com/anaconda/pkgs/r
ssl_verify: false
```
然后执行下面命令
```
conda clean -i
conda install tqdm -f 
```

> 其他的相关命令:
```
conda clean -i 清除索引缓存，保证用的是镜像站提供的索引。
conda info -e 查看虚拟环境
conda create -n name 创建虚拟环境
 
conda update conda
conda update anaconda                  //超级慢,12小时未成功，放弃！
conda update anaconda-navigator
conda update --all
 
 
1、正激活：source ~/anaconda3/bin/activate       //激活anaconda linux下
 
2、升级conda：conda update conda                 //升级Anaconda前必须先升级conda
 
3、升级anaconda：conda update anaconda
                conda update anaconda-navigator
 
4、升级指定软件，例如spyder：conda update spyder
 
5、更新所有包：conda update --all //所有的环境都更新
 
6、安装包：conda install packageName
 
7、更新包：conda update packageName
 
8、查询包：conda update -h
 
9、反激活：conda deactivate
```
# 最后
但由于conda之前的一次大更新导致无论你怎么更新都更新不完，博主就是五一期间更新了一个星期，电脑都不敢碰一下愣是进度卡在那里没动

后面实在不想在等了，通过直接下载相应版本安装包对Anconda进行更新，

由于博主是Windows系统的电脑，所以将原本配置好的环境变量进行删除，

通过 `此电脑`右键-->`属性`-->`高级系统设置`-->`环境变量`-->系统变量中的`Path`

![](https://image.ahao.ah.cn/83692d59173de0e95f27b59675e423b.png)

将这三个配置好了之后，返回的时候记得按确定就可以了，不过好像要重启电脑才会生效

最后打开终端输入`python`查看是否更新成功

由于博主比较懒，所以就不顺便把安装步骤给弄出来了，如果有需要可以[百度](https://www.baidu.com/)进行查询相关步骤

或者通过其他博主的[Anaconda下载及安装详细教程](http://t.csdn.cn/2yeiq)进行安装

博主使用的python3.8安装包地址：
[Anconda安装包](https://repo.anaconda.com/archive/Anaconda3-2021.05-Windows-x86_64.exe)


anconda官网：
[官网](https://www.anaconda.com/download/)

# 总结

更新最好还是直接通过官网进行下载更快一点，整个过程甚至都不用半个小时


{% hideToggle 封面图片 %}
![](https://image.ahao.ah.cn/09551233ad4cd71ad280182d515a793.jpg)
{% endhideToggle %}


### 如果觉得该文章对您有帮助，或者需要补充的内容可以在下方留言或者你的博客地址，博主有看到会回访哦QVQ！

感谢您的观看，欢迎下次再见，拜拜
----------------------------------------------------------------------