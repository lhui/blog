---
title: '[创造CLI系列]NodeJS环境搭建'
author: Li Hui
type: post
date: 2020-09-24T00:00:14+00:00
url: /create-cli-application-1.html
views:
  - 763
bot_views:
  - 2071
categories:
  - CLI应用
  - 从0到1
tags:
  - CLI
  - 从0到1

---
# 前言

前面我们看了cli应用的好处和方便之处（不用左右点击，当然方便也是相对的，无非是将任务交给了谁，这其实就和记录软件快捷键和使用鼠标进行层级选择一样，其实都可以实现同样的功能，只是渠道不一样罢了），本问我们开始创建我们的第一个CLI应用，第一步搭建所需要的环境，本系列预估使用NodeJS进行搭建，估计后期会尝试使用Go进行搭建，本文章主要记录NodeJS的安装

# 步骤

写作本文的时候采用的是Mac 电脑，Windows电脑更为简单，一样的道理

## 下载软件

上述的两个位置都可以下载 本文章采用下面的箭头所指的12.18.4 诶 我记得当时的稳定版本还是8

![image-20200923213932494][1] 

然后和其他的安装器一样安装即可(一步一步往下走即可)

![image-20200923214313628][2] 

![image-20200923214357600][3] 

![image-20200923214458778][4] 

## 校验是否成功

打开命令行工具 需要检测node和npm是否生效

输入

<pre><code class="language-bash">$ node --version</code></pre>

返回结果如下

![image-20200923214816446][5] 

当我们看到返回的 `v**.**.*`的时候证明我们已经安装好了NodeJS的环境

检测npm 是否生效

命令行

<pre><code class="language-bash">$ npm --version</code></pre>

是否生效和上面的类似 返回结果如下图

![image-20200923215155881][6] 

# 总结

NodeJS的环境还是比较简单进行安装的，电脑上也不需要多少配置，今天就算是项目开始启动了，开始创建第一个CLI应用。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923213932494.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923214313628.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923214357600.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923214458778.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923214816446.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200923215155881.png