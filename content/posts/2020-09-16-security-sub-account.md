---
title: '[安全相关]使用腾讯云子账号提高账号安全性'
author: Li Hui
type: post
date: 2020-09-16T15:05:08+00:00
url: /security-sub-account.html
views:
  - 1213
bot_views:
  - 1251
categories:
  - 安全
tags:
  - 安全
  - 权限
  - 腾讯云

---
# 前言

为什么使用子账号呢？

子账号可以提高安全性，如果我们采用主账号的key进行授权的时候，其他人一旦获取到我们的key，便对我们形成致命的打击，如果我们采用子账号，一方面，我们可以快速的撤销授权，避免损失，在最差的情况下，我们保证受损的是最少的，这些不妨事一种容灾的好方法。此处仅书写了腾讯云的系统，未涉及到其他的系统，在安全的角度上应该各个系统都有相应的系统，此处仅以腾讯云为例。

# 步骤

## 首先登陆账号

首先在腾讯云的网站上登陆你的账号 <a href="https://cloud.tencent.com/" target="_blank"  rel="nofollow" >https://cloud.tencent.com/</a>

## 进入腾讯云的子账号访问管理系统

<a href="https://cloud.tencent.com/" target="_blank"  rel="nofollow" >https://cloud.tencent.com/</a>

## 创建相对应的账号

![Za8YHR][1] 

也就是上面的用户 ，点击创建用户

进入下述的界面

![7lapp2][2] 

此处选择快速创建（因为此处未涉及到重要的步骤，快速过）

会看到下属的界面 拥有四个项目 用户名 访问方式 用户权限 和可接受消息类型

用户名随意 按照自己喜好即可

![nS47XW][3] 

访问方式 软件使用的话可以采用编程登陆（仅允许编程登陆更安全一点）

![image-20200916225400820][4] 

用户权限 选择你要为子用户分配的权限 比如此处仅授权COS的操作（用于操作对象存储 比如图床等等使用方式）

![7JzgGZ][5] 

可接受消息类型 为下述的这几种 比较容易理解（如果为命令行使用的话，此处均不需要）

![cLpiwq][6] 

![Z0ZWsF][7] 

验证安全方式 即可以创建新的用户

**最后的最后 还希望妥善保管好你的key**

![Si1akU][8] 

# 总结

安全问题，无论何时都是大问题，提早一步进行解决，可以减轻后面的慌张，还是希望在读的你不会出现安全性的问题。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/Za8YHR.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/7lapp2.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/nS47XW.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200916225400820.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/7JzgGZ.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/cLpiwq.png
 [7]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/Z0ZWsF.png
 [8]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/Si1akU.png