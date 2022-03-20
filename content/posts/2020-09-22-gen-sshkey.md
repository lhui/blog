---
title: '[安全系列]生成ssh证书'
author: Li Hui
type: post
date: 2020-09-22T00:00:39+00:00
excerpt: 生成ssh证书有什么作用，首先可以快速的登陆服务器，无需每次数输入密码，只需要配置一次ssh证书即可，即可以直接通过ssh登陆证书，借此用处我们可以使用ssh证书对git仓库进行操作，无需要每次上载的时候都需要输入密码，输密码想想都麻烦，再说谁不想简单一点呢？
url: /gen-sshkey.html
views:
  - 541
bot_views:
  - 1104
categories:
  - 安全
tags:
  - SSH

---
# 前言

生成ssh证书有什么作用，首先可以快速的登陆服务器，无需每次数输入密码，只需要配置一次ssh证书即可，即可以直接通过ssh登陆证书，借此用处我们可以使用ssh证书对git仓库进行操作，无需要每次上载的时候都需要输入密码，输密码想想都麻烦，再说谁不想简单一点呢？

而且这步骤很简单。此处记录以下指令，以便后续查看。

# 内容

因为本步骤记录的是生成证书的代码 这就很简单了，不需要太多的代码，生成证书的前置条件是需要有openssh.Linux/Mac预置了相关的软件，Windows用户只需要安装Git即可。<a href="https://git-scm.com/" target="_blank"  rel="nofollow" >https://git-scm.com/</a>

**注： 自版本1803起，<a href="https://en.wikipedia.org/wiki/Windows_10" target="_blank"  rel="nofollow" >Windows 10中</a>已包含基于<a href="https://en.wikipedia.org/wiki/OpenSSH" target="_blank"  rel="nofollow" >OpenSSH</a>的客户端和服务器程序。默认情况下，SSH客户端和密钥代理已启用并可用，并且SSH服务器是可选的按需功能。**

![n5tfyK][1] 

图源：wikipedia

**最重要的步骤：生成证书 可以生成不带邮箱的和带邮箱，下面先给出带邮箱的，而后给一个不带邮箱的**

带邮箱的(来源：<a href="https://docs.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent" target="_blank"  rel="nofollow" >https://docs.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent</a>)

<pre><code class="language-bash">$ ssh-keygen -t rsa -b 4096 -C &quot;your_email@example.com&quot;</code></pre>

执行该命令后会显示你的要储存的位置

<pre><code class="language-bash">Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter]</code></pre>

此时一般选择默认即可 文件保存在/Users/you/.ssh/id\_rsa（Mac） /home/you/.ssh/id\_rsa(Linux) /c/Users/you/.ssh/id_rsa(Windows)

中 而后要求输入安全密码

<pre><code class="language-bash">&gt; Enter passphrase (empty for no passphrase): [Type a passphrase]
&gt; Enter same passphrase again: [Type passphrase again]</code></pre>

此时最好输入安全密码，可以多一层保障，即使你的证书丢了也不必担心安全问题，当然不输入密码也是可以的

此时密钥已经在相应的位置生成，可以进行其他的操作。

下面为不是输入密码的，直接省去一个参数即可。其他的操作相同

<pre><code class="language-bash">$ ssh-keygen -t rsa -b 4096</code></pre>

# 总结

生成ssh-key是一个非常简单的事情，通过这个简单的事情，可以为以后的事情增加工作效率，不得不说是一个一劳永逸的事情。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/n5tfyK.jpg