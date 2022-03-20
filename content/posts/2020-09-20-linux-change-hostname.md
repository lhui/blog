---
title: '[linux系列] 修改主机用户名'
author: Li Hui
type: post
date: 2020-09-20T07:19:54+00:00
url: /linux-change-hostname.html
views:
  - 470
bot_views:
  - 370
categories:
  - Linux
tags:
  - Linux

---
# 前言

使用腾讯云 阿里云 Google Cloud AWS AZURE 等等云厂商 默认给的用户名都是很奇怪的 一点都没意思，也没得生产力（好像有了好名字就有生产力一样）本问介绍的是，将主机名修改为自己定义的。

# 步骤

可以有几种情况修改，仅在本次启动前起效果，永久起效果这两种情况。

## 本次生效

命令行

<pre><code class="language-bash">sudo hostname {{hostname}} # 后面的名字为你想修改的名字</code></pre>

重启终端生效 但是重启后失效

## 长期生效（需要重启）

命令行

<pre><code class="language-bash">sudo vi /etc/hostname</code></pre>

在文件中填写你想要修改的名字即可

而后输入： 在输入wq(保存并退出)保存并退出

此时便可以重启 修改即可生效

# 总结

这个比较简单 可能有问题的在于vi命令行，先挖个坑，以后慢慢填（😂