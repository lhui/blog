---
title: '[Linux]Ubuntu安装宝塔面板'
author: Li Hui
type: post
date: 2021-01-03T15:56:30+00:00
url: /install-bt-panel.html
views:
  - 2154
bot_views:
  - 335
categories:
  - Linux
tags:
  - Linux

---
# 准备:

  1. 服务器一个(本机虚拟机也可以)
  2. 上网环境
  3. SSH软件(Putty || Xshell)

# 涉及网址:

  1. https://www.bt.cn/
  2. https://www.netsarang.com/zh/xshell/
  3. https://www.putty.org/

# 安装步骤:

## 1. 购买服务器 || 打开虚拟机

这一步骤比较简单,略过

## 2. 连接SSH

下载SSH软件,安装,这一步骤比较简单,略过

## 3. 安装宝塔

<a class="wp-editor-md-post-content-link" href="https://www.bt.cn/" target="_blank"  rel="nofollow" >宝塔首页</a>选择对应的系统,选择下面的立即安装

![image-20210103182035280][1] 

选择合适的Linux发行版 本文使用的Ubuntu ,不过我更推荐CentOS(本文时间2021年1月3日 CentOS正在经历变革,以后可能会有新的稳定发行版),点击复制代码即可

![image-20210103182329523][2] 

打开SSH客户端,并连接服务器

将上述复制的内容粘贴 根据提示进行操作,下面的地方输入y即可

![image-20210103182623014][3] 

最终会出现 下面的提示 面板地址和username 和password 关键信息此处打码 **注意在相应的内容服务商开通8888端口的TCP协议访问权限**

![image-20210103184806088][4] 

输入面板地址 进行访问(若此时访问时间过长,或者地址无法访问,请在此查看是否在服务商中放行了8888端口) 而后出现下面的画面证明安装面板成功

![image-20210103185143029][5] 

## 安装LNPM环境

同意协议后 推荐安装第一个LNMP的环境

![image-20210103185328658][6] 

等待程序安装完成即可

![image-20210103185423377][7] 

# 总结

宝塔的安装还是相对来说比较简单的,总结下来需要一下的步骤, 1. 购买服务器 2. 安装SSH软件并登录到服务器 3. 安装宝塔的环境 4. 安装LNPM的环境.

此处注意:

  1. 当不需要面板服务进行操作的时候推荐在后台关闭掉面板服务,宝塔面板出现严重性的问题,至少已经发生了两次了,数据安全一定要保证.
  2. 注意修改SSH端口 SSH端口一定不要用22 端口 现在有很多工具可以扫描22号端口 修改为其他的端口 防止被扫描

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103182035280.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103182329523.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103182623014.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103184806088.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103185143029.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103185328658.png
 [7]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210103185423377.png