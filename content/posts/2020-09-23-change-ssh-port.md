---
title: '[Linux系列]修改SSH端口 防止端口扫描'
author: Li Hui
type: post
date: 2020-09-23T00:00:57+00:00
url: /change-ssh-port.html
views:
  - 1200
bot_views:
  - 261
categories:
  - Linux
tags:
  - Linux

---
# 前言

网络上开的服务器，只要是大的厂商的服务器，都免不了受到很多机器的自动扫描，自动尝试登录，这就很头疼，有几个比较好的方法，第一个只允许特定IP登录（这种方法有些问题，尤其是个人很难申请到固定的外网ip地址（内网不算，内网不会还有人扫描把。。）），还有一种较为常用的方法是修改SSH端口，**一定要注意，修改SSH端口的时候，一定要先使用新的客户端进行登录成功后，再关掉原来的连接，否则有可能修改失败，无法连接到服务器，别问我咋知道的**

# 步骤

这个步骤分为三部分 修改sshd_config配置文件，重启ssh服务（并非服务器），检测效果并注释掉原本端口。

## 修改sshd_config文件

sshd\_config文件在 /etc/ssh/sshd\_config 使用下面的命令编辑

<pre><code class="language-bash">vi /etc/ssh/sshd_config</code></pre>

![image-20200922193915452][1] 

在此处下面添加Port {{你想改的端口号}}(提示：vi中输入i进度编辑模式)

我修改的如下图所示

![image-20200922194141597][2] 

使用ESC ->:->wq保存

## 重启服务

CentOS7重启ssh服务

<pre><code class="language-bash">systemctl restart ssh</code></pre>

## 测试连接情况并注释原来的端口

**注意：此时一定要注意开启服务商的防火墙，服务商一般都有各自的防火墙，一定要注意开，否则无法使用。**

使用新的端口登陆 比如我这里是22011

命令行如下 使用工具是一样的

<pre><code class="language-bash">ssh -p {{port}} {{username}}@{{ServerIP}}</code></pre>

比如我的

<pre><code class="language-bash">ssh -p 22011 lihui@192.168.1.10 # ip和你的可能不同，如有雷同 纯属巧合</code></pre>

此时如果连接成功就可以注释掉原来的端口并使用防火墙关闭掉22号端口(双重保障) 注意：发现的问题 **腾讯云轻量云22号端口是本来就是注释掉的 但是 还是可以使用**

![image-20200922200951133][3] 

此时大功告成 再也没有几万次尝试登陆的信息了。

# 总结

端口扫描解决起来很麻烦，毕竟对机器扫描的不是真实的人，也是机器，而且机器还无休，所以最好的办法就是修改端口和修改准入ip（也可以使用跳板机），使用这种方法可以大大的减少被爆破的几率。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200922193915452.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200922194141597.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200922200951133.png