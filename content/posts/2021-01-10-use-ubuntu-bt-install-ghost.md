---
title: 使用Ubuntu 及宝塔搭建Ghost平台
author: Li Hui
type: post
date: 2021-01-10T07:51:36+00:00
url: /use-ubuntu-bt-install-ghost.html
views:
  - 2174
bot_views:
  - 870
categories:
  - Linux
tags:
  - Ghost
  - Linux
  - 宝塔

---
说明:

> 安装Ghost博客的步骤比较多一点，在此记录下，以备以后学习与检查。 

所需:

  1. 服务器或者本地虚拟机*1
  2. SSH 软件*1
  3. 电脑*1

# 安装步骤

## 1. 安装宝塔面板

这一步骤在上一篇文章发表过,可以查看一下上一篇的文章

## 2. 配置安装Ghost

### 1. 首先使用SSH软件连接实例

这个简单，直接在XShell 或者Putty中填写服务器的信息即可

### 2. 创建新用户 本文以ghoster为例

切换到Root权限下：

<pre><code class="language-bash line-numbers">adduser ghoster
</code></pre>

![image-20210110071637122][1] 

为新用户 增加 sudo权限

<pre><code class="language-bash line-numbers"># usermod -aG sudo ghoster
</code></pre>

切换到ghoster用户 并确定sudo权限

<pre><code class="language-bash line-numbers"># su ghoster
# sudo su
</code></pre>

![image-20210110071952094][2] 

如上图所示 # 开头则表明已经具有sudo 权限

### 3. 更新安装包

使用ghoster 更新系统

直接使用上面的用户root更新服务器即可

<pre><code class="language-bash line-numbers"># sudo apt-get update
# sudo apt
</code></pre>

可能会出现下面的情况 直接点击回车即可

![image-20210110072305254][3] 

### 4. 软件安装（本处只需要安装NodeJS即可，其他软件宝塔面板已经安装上）

本处只需要安装Node.JS即可，其他的环境（Nginx, MySQL）使用宝塔面板已经安装上

加入源

<pre><code class="language-bash line-numbers">curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash
</code></pre>

安装NodeJS

<pre><code class="language-bash line-numbers">sudo apt-get install -y nodejs
</code></pre>

### ５.安装配置Ghost

安装Ghost

<pre><code class="language-bash line-numbers">sudo npm install ghost-cli@latest -g
</code></pre>

切换到/www/wwwroot/目录下（为了查找的时候方便，原则上任何一个可以操作的目录均可），进行安装配置

切换目录

<pre><code class="language-bash line-numbers">cd /www/wwwroot
</code></pre>

创建文件夹 ghost

<pre><code class="language-bash line-numbers">sudo mkdir ghost
</code></pre>

为ghoster用户配置此文件夹的权限

<pre><code class="language-bash line-numbers">sudo chown ghoster:ghoster /www/wwwroot/ghost
</code></pre>

修改文件夹权限

<pre><code class="language-bash line-numbers">sudo chmod 775 /www/wwwroot/ghost
</code></pre>

进入文件夹安装程序（此时用户仍为ghoster）

<pre><code class="language-bash line-numbers">cd /www/wwwroot/ghost/
</code></pre>

开始使用ghost-cli安装ghost 博客

前期准备 在宝塔中创建新的数据库

![image-20210110084937179][4] 

开始安装Ghost

<pre><code class="language-bash line-numbers">$ ghost install
</code></pre>

此时注意 当需要进行Ngnix的配置的时候输入N (此处不需要进行Nginx的配置),一会我们使用宝塔对Nignx进行配置

安装结束后 会默认采用2368端口进行监听 注意显示的端口 如果不知道的化 可以查看安装目录的config.production.json 的port字段即可

## 3. 配置代理+SSL证书

这一个步骤的主要目的是使用宝塔面板直接对相应的服务进行反向代理, 将对口映射到网址上,确保网址可以使用,通知配置SSL证书,保证网站可以安全传输信息.

首先第一步 配置证书

![image-20210110154403350][5] 

点击文件验证即可,简单快速

![image-20210110154535967][6] 

按照顺序添加信息即可 目标URL根据上一步骤的端口号码填写即可.

而后就可以访问网址对应用进行访问,进行配置即可.

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110071637122.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110071952094.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110072305254.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110084937179.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110154403350.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210110154535967.png