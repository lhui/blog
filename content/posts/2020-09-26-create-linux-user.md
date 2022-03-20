---
title: '[Linux系列]创建Linux用户'
author: Li Hui
type: post
date: 2020-09-26T15:46:58+00:00
url: /create-linux-user.html
views:
  - 486
bot_views:
  - 315
categories:
  - Linux
tags:
  - Linux

---
# 前言

如果直接在Linux中使用root账户,真的十分危险,root拥有最高的权限,一方面如果安装其他的软件,虽然说是畅通无阻,但是与之同时带来的问题是,如果一旦账户让其他人拿到,岂不是很危险,因此推荐采用先创建的账户进入,特殊的时候采用切换到root以保证服务器的安全.

# 步骤

# 创建用户

创建用户是一个重要的问题 当然也特别的简单

<pre><code class="language-bash"># adduser {{username}} # 此时不但创建了用户 还为用户创建了一个和他名字一样的用户组（groups）</code></pre>

为用户设定密码

<pre><code class="language-bash"># passwd {{username}} # 而后根据相应的提示输入密码即可</code></pre>

一般推荐是新的服务器首先创建新的组,再在组的基础上创建新的用户,这样子的话比较稳妥,

## 创建用户组

命令行

<pre><code class="language-bash">$ sudo groupadd {{groud_name}} # 后面的为组的名字</code></pre>

如果现在是root账户 且命令行前的是#(sharp) 可以直接使用

<pre><code class="language-bash"># groupadd {{username}}</code></pre>

示例:

<pre><code class="language-bash">$ sudo groupadd devGroup</code></pre>

查看所有的用户组

<pre><code class="language-bash"># cat /etc/group</code></pre>

返回信息：(一般不要截这张图，这张图会暴露你所有的用户组，我这是开发测试机器，随时重置系统所以无所谓)

![image-20200926233604960][1] 

## 创建一个新用户到用户组中

命令行

<pre><code class="language-bash"># usermod -a -G {{groupName}} {{userName}}</code></pre>

示例：

<pre><code class="language-bash"># usermod -a -G devGroup devor </code></pre>

检测是否生效

<pre><code class="language-bash">$ groups</code></pre>

返回信息：

![2KUmgT][2] 

# 总结

创建用户的目的在于什么呢？ 有的是不同的用户操作不同的内容，将用户相互隔离，有的是为了安全起见，就和操作系统一样，如果都是一个root，一个新手 用户直接rm了 岂不是很恐怖，而且也极大的保护了用户的内容不被其他人看到。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200926233604960.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/2KUmgT.png