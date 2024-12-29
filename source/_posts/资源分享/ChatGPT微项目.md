---
title: ChatGPT微信ai版
categories: 资源分享
tags:
  - AHao
  - chatgpt
  - 微信
cover: 'https://image.ahao.ah.cn/b0c192a6d2bf3b4b531bc680a2f43ad.jpg'
ai: true
abbrlink: d5da
date: 2023-12-09 01:50:59
---

# 前言
由于太多人问如何在`微信`上使用ChatGPT,故而有了写这篇`新手村教程`文章的想法
此文章内容需要`魔法`以及有一点看懂代码的能力，由于该项目需要用到`python`，具体操作可以看`python`相关的安装教程，当然不会也没关系，该博主已经跟[百度](https://baidu.com)深度合作
魔法问题请自行解决，实在不会再找博主


# 前期准备
Chatgpt微项目地址：https://github.com/zhayujie/chatgpt-on-wechat?tab=readme-ov-file
1. 账号注册
项目默认使用OpenAI接口，需前往 [OpenAI注册页面](https://beta.openai.com/signup) 创建账号，创建完账号则前往 [API管理页面](https://beta.openai.com/account/api-keys) 创建一个 API Key 并保存下来，后面需要在项目中配置这个key。接口需要海外网络访问及绑定信用卡支付。

默认对话模型是 openai 的 gpt-3.5-turbo，计费方式是约每 1000tokens (约750个英文单词 或 500汉字，包含请求和回复) 消耗 $0.002，图片生成是Dell E模型，每张消耗 $0.016。

项目同时也支持使用 LinkAI 接口，无需代理，可使用 文心、讯飞、GPT-3、GPT-4 等模型，支持 定制化知识库、联网搜索、MJ绘图、文档总结和对话等能力。修改配置即可一键切换，参考 [接入文档](https://link-ai.tech/platform/link-app/wechat)

2. 运行环境
支持 Linux、MacOS、Windows 系统(可在Linux服务器上长期运行)，同时需安装 Python。
Python版本：建议Python版本在 3.7.1~3.9.X 之间，推荐3.8版本，3.10及以上版本在 MacOS 可用，其他系统上不确定能否正常运行。

(1) 克隆项目代码：
```
git clone https://github.com/zhayujie/chatgpt-on-wechat
cd chatgpt-on-wechat/
```

(2) 安装核心依赖 (必选)：

能够使用itchat创建机器人，并具有文字交流功能所需的最小依赖集合。
```
pip3 install -r requirements.txt
```
(3) 拓展依赖 (可选，建议安装)：
```
pip3 install -r requirements-optional.txt
```
如果某项依赖安装失败请注释掉对应的行再继续。

其中tiktoken要求python版本在3.8以上，它用于精确计算会话使用的tokens数量，强烈建议安装。
```
使用google或baidu语音识别需安装ffmpeg，

默认的openai语音识别不需要安装ffmpeg。
```


使用azure语音功能需安装依赖，并参考文档的环境要求。 :
```
pip3 install azure-cognitiveservices-speech

```
# 配置
配置文件的模板在根目录的config-template.json中，需复制该模板创建最终生效的 config.json 文件：
```
  cp config-template.json config.json
```
然后在config.json中填入配置，以下是对默认配置的说明，可根据需要进行自定义修改（请去掉注释）：

# config.json文件内容示例
```
{
  "open_ai_api_key": "YOUR API KEY",                          # 填入上面创建的 OpenAI API KEY
  "model": "gpt-3.5-turbo",                                   # 模型名称, 支持 gpt-3.5-turbo, gpt-3.5-turbo-16k, gpt-4, wenxin, xunfei
  "proxy": "",                                                # 代理客户端的ip和端口，国内环境开启代理的需要填写该项，如 "127.0.0.1:7890"
  "single_chat_prefix": ["bot", "@bot"],                      # 私聊时文本需要包含该前缀才能触发机器人回复
  "single_chat_reply_prefix": "[bot] ",                       # 私聊时自动回复的前缀，用于区分真人
  "group_chat_prefix": ["@bot"],                              # 群聊时包含该前缀则会触发机器人回复
  "group_name_white_list": ["ChatGPT测试群", "ChatGPT测试群2"], # 开启自动回复的群名称列表
  "group_chat_in_one_session": ["ChatGPT测试群"],              # 支持会话上下文共享的群名称  
  "image_create_prefix": ["画", "看", "找"],                   # 开启图片回复的前缀
  "conversation_max_tokens": 1000,                            # 支持上下文记忆的最多字符数
  "speech_recognition": false,                                # 是否开启语音识别
  "group_speech_recognition": false,                          # 是否开启群组语音识别
  "use_azure_chatgpt": false,                                 # 是否使用Azure ChatGPT service代替openai ChatGPT service. 当设置为true时需要设置 open_ai_api_base，如 https://xxx.openai.azure.com/
  "azure_deployment_id": "",                                  # 采用Azure ChatGPT时，模型部署名称
  "azure_api_version": "",                                    # 采用Azure ChatGPT时，API版本
  "character_desc": "你是ChatGPT, 一个由OpenAI训练的大型语言模型, 你旨在回答并解决人们的任何问题，并且可以使用多种语言与人交流。",  # 人格描述
  # 订阅消息，公众号和企业微信channel中请填写，当被订阅时会自动回复，可使用特殊占位符。目前支持的占位符有{trigger_prefix}，在程序中它会自动替换成bot的触发词。
  "subscribe_msg": "感谢您的关注！\n这里是ChatGPT，可以自由对话。\n支持语音对话。\n支持图片输出，画字开头的消息将按要求创作图片。\n支持角色扮演和文字冒险等丰富插件。\n输入{trigger_prefix}#help 查看详细指令。",
  "use_linkai": false,                                        # 是否使用LinkAI接口，默认关闭，开启后可国内访问，使用知识库和MJ
  "linkai_api_key": "",                                       # LinkAI Api Key
  "linkai_app_code": ""                                       # LinkAI 应用code
}
```

# 配置说明：

1. 个人聊天

个人聊天中，需要以 `"bot"或"@bot"` 为开头的内容触发机器人，对应配置项 `single_chat_prefix` (如果不需要以前缀触发可以填写 `"single_chat_prefix": [""]`)
机器人回复的内容会以 `"[bot]"` 作为前缀， 以区分真人，对应的配置项为 `single_chat_reply_prefix` (如果不需要前缀可以填写 `"single_chat_reply_prefix": ""`)

2. 群组聊天
群组聊天中，群名称需配置在 `group_name_white_list`  中才能开启群聊自动回复。如果想对所有群聊生效，可以直接填写 `"group_name_white_list": ["ALL_GROUP"]`
默认只要被人 `@` 就会触发机器人自动回复；另外群聊天中只要检测到以 `"@bot"` 开头的内容，同样会自动回复（方便自己触发），这对应配置项 `group_chat_prefix`
可选配置: `group_name_keyword_white_list`配置项支持模糊匹配群名称，`group_chat_keyword`配置项则支持模糊匹配群消息内容，用法与上述两个配置项相同。

`group_chat_in_one_session`：使群聊共享一个会话上下文，配置 `["ALL_GROUP"]` 则作用于所有群聊

3. 语音识别

添加 `"speech_recognition"`: `true` 将开启语音识别，默认使用`openai`的`whisper`模型识别为文字，同时以文字回复，该参数仅支持私聊 (注意由于语音消息无法匹配前缀，一旦开启将对所有语音自动回复，支持语音触发画图)；
添加 `"group_speech_recognition"`: `true` 将开启群组语音识别，默认使用`openai`的`whisper`模型识别为文字，同时以文字回复，参数仅支持群聊 (会匹配`group_chat_prefix`和`group_chat_keyword`, 支持语音触发画图)；
添加 `"voice_reply_voice"`: `true` 将开启语音回复语音（同时作用于私聊和群聊），但是需要配置对应语音合成平台的`key`，由于`itchat`协议的限制，只能发送语音mp3文件，若使用`wechaty`则回复的是微信语音。

4. 其他配置

`model`: 模型名称，目前支持 `gpt-3.5-turbo, text-davinci-003, gpt-4, gpt-4-32k, wenxin , claude , xunfei`(其中`gpt-4 api`暂未完全开放，申请通过后可使用)
`temperature,frequency_penalty,presence_penalty`: `Chat API`接口参数，详情参考`OpenAI`官方文档。
`proxy`：由于目前 `openai` 接口国内无法访问，需配置代理客户端的地址，详情参考官方文档
对于图像生成，在满足个人或群组触发条件外，还需要额外的关键词前缀来触发，对应配置 `image_create_prefix` 
关于`OpenAI`对话及图片接口的参数配置（内容自由度、回复字数限制、图片大小等），可以参考 对话接口 和 图像接口 文档，在`config.py`中检查哪些参数在本项目中是可配置的。
`conversation_max_tokens`：表示能够记忆的上下文最大字数（一问一答为一组对话，如果累积的对话字数超出限制，就会优先移除最早的一组对话）
`rate_limit_chatgpt，rate_limit_dalle`：每分钟最高问答速率、画图速率，超速后排队按序处理。
`clear_memory_commands`: 对话内指令，主动清空前文记忆，字符串数组可自定义指令别名。
`hot_reload:` 程序退出后，暂存微信扫码状态，默认关闭。
`character_desc` 配置中保存着你对机器人说的一段话，他会记住这段话并作为他的设定，你可以为他定制任何人格 (关于会话上下文的更多内容参考该 `issue`)
`subscribe_msg`：订阅消息，公众号和企业微信`channel`中请填写，当被订阅时会自动回复， 可使用特殊占位符。目前支持的占位符有`{trigger_prefix}`，在程序中它会自动替换成`bot`的触发词。

# 特别提醒
> ps:如果上方内容都看不懂的话，下面我会尽可能的简单化，以下的所有内容都是基于本地部署

1. 如果没有安装`git`可以在项目直接点击下载压缩安装包到本地进行解压(可以放在桌面或者D盘下新建一个文件夹)
![](https://image.ahao.ah.cn/ee9b2296cc6d6ce2686caca5f6ded72.png)

到这里恭喜你，你离成功已经进了一步啦！！！
![](https://image.ahao.ah.cn/797c7a1a23c57ec42d34289340879da.png)

2. 点进文件查看是否有`config.json`文件，如果没有的话可以在文件上方直接输入`cmd`回车打开终端命令窗口
![](https://image.ahao.ah.cn/2f3e6c9eb8cf7c61a630c2f031cb27e.png)
输入`cp config-template.json config.json` 进行拷贝，也可以将文件`config-template.json`直接复制重命名为 `config.json` 即可
![](https://image.ahao.ah.cn/eda6b7c8c077d29b8eaa176838e02e8.png)

3. 这里考虑到有部分同学可能没有`openai`账号，所以在这里再推荐一个项目`GPT_API_fre`，获取一个免费的`api`
》》》博主极度推荐使用
项目地址：https://github.com/chatanywhere/GPT_API_free?tab=readme-ov-file
点击`项目地址` --> 滑到下方点击`申请免费的key` ---> 将你的key:`'sk-xxxxxxx'`进行保存
![](https://image.ahao.ah.cn/06070db17d769d5be8c8c1abeb2064a.png)
这样你就拥有专属于自己的`api key`了
![](https://image.ahao.ah.cn/b3504ea8b95b10868dccfbd26405438.png)
还有这里需要注意的，需要在`config.json`文件中需要添加下面这一句，在项目的下可以看到
![](https://image.ahao.ah.cn/43017d89f13095582947c2ce5579b3c.png)
```
openai.api_base = "https://api.chatanywhere.tech/v1"
```
> 注意：链接最后面的`/v1`一定要加

4. 接下来可以打开你的`VSCode`或者`pycharm`编译器对文件进行配置，当然也可以用`文本`打开`config.json`文件进行编写
![](https://image.ahao.ah.cn/f96bbf87bba896adac74f0997627389.png)

5. 可以看到上方的`json`文件中缺少了`openai.api_base`设置，自己添加即可
由于博主是一个`追求简约(懒得折腾)`的人，所获取的`api key`是上方项目的，由于该项目在国内中转可以不需要`魔法`，将json中的`"proxy": ""`设置修改为空或者默认即可

如果用的是自己的`openai key`则添加为获取`key`的官网网址即可,启动项目时则需要开启`魔法`
![](https://image.ahao.ah.cn/6a27f79bf180dbbadff51d6566ee6a7.png)

上方图片中`"hot_reload": true`为热启动，建议打开，除了第一次启动项目需要扫码之后就不用再每次都重复扫码登录，建议是打开

其他设置都可以在`config.py`文件中找到

6. 上面设置好之后我们点击进入项目文件，在文件上方输入`cmd`回车运行打开终端
![](https://image.ahao.ah.cn/2f3e6c9eb8cf7c61a630c2f031cb27e.png)

7. 接下来我们开始安装依赖
- 复制下方命令安装核心依赖 (必选)：

- 能够使用itchat创建机器人，并具有文字交流功能所需的最小依赖集合。
```
pip3 install -r requirements.txt
```
- 拓展依赖 (可选，建议安装)：
- 安装拓展依赖之后，就可以装一些其他的插件对机器人的功能进行优化(后续可能会单独另外写一篇文章)
```
pip3 install -r requirements-optional.txt
```
复制上方命令回车即可
![](https://image.ahao.ah.cn/cee6ad393a7a0acfcfa1f3720d682e5.png)

由于很多库都是国外的，所以在命令后面建议添加：`-i https://pypi.tuna.tsinghua.edu.cn/simple`进行换源安装

```
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip3 install -r requirements-optional.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```
换源安装后速度会快很多，第一次安装可能会失败，再重新安装就好了

8. 之后在命令窗口中继续输入`py app.py`进行启动
![](https://image.ahao.ah.cn/afa88ddd5762886c08016a367109d29.png)
然后扫码进行登录即可
![](https://image.ahao.ah.cn/526da6f8376d09d76c0d92807833202.png)

# 特别注意：
电脑中不要登录你扫码的微信号，以及由于存在封号的可能性，所以建议是拿小号进行测试


# 其他原因
如果上方教程看完之后还实在不会，那。。。。
可以在下方给`博主留言`进行远程安装

由于该项目需要电脑`24小时`都开着
后续可能会更新白嫖云电脑的教程，可以让你的电脑无需一直开着


# 最后
如果该文章对你有所帮助，可以在下方对博主进行打赏投喂
感谢您的支持，后续再会~~

