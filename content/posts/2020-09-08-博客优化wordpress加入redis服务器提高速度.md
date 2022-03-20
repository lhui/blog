---
title: '[博客优化]Wordpress加入redis服务器提高速度'
author: Li Hui
type: post
date: 2020-09-08T13:52:55+00:00
url: /博客优化wordpress加入redis服务器提高速度.html
views:
- 1213
  bot_views:
- 484
  categories:
- 博客优化
  tags:
- 博客优化

---
# 为什么要使用redis

Redis 是一个基于内存的数据库管理系统，相对于mysql等数据库，拥有读取速度快的有点，相比于mysql直接从硬盘中够读取数据，从内存中读取数据的效率会变得快的多。

采用Redis可以大幅度的提高网页的首屏速度，当然提高Wordpress的首屏速度的方法有很多，比如静态化等等，当然这都是后话，本次记录的是采用redis提高网页的访问速度。

# 安装设置过程

本次的机器配置：

1. CentOS 7 腾讯云轻量云服务器一台
2. 终端软件一个（可以直接使用网页）

## 安装redis(推荐采用yum源)

### 加入epel源

<pre><code class="language-bash">sudo yum install epel-release
sudo yum update #update the source 此时可能会花费一些时间</code></pre>

### 安装redis

<pre><code class="language-bash">sudo yum -y install redis</code></pre>

### 启动服务

<pre><code class="language-bash">sudo systemctl start redis # 此处注意加sudo</code></pre>

此时不会显示任何信息

此时redis的服务已经启动 可以使用redis-cli进入命令行模式 进行测试 比较可爱的ping pong 就出现了

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/blog-redis-ping-pong.png)
## Wordpress加入插件

我采用的是下面的插件（下载数量比较高）

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/blog-wordpress-redis-plugin.png)

## 进行配置

进入插件的设置界面 点击 Enable Object Cache
![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/blog-wordpress-redis-plugin-enable.png)

启动后会自动进行连接 当发现connected的时候证明连接成功

# 速度对比

### 加入缓存前（2020-09-08 21:23）

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/blog-wordpress-add-redis-before.png)

## 加入缓存后 （2020-09-08 21:31）

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/blog-wordpress-add-redis-after.png)

# 结论

经过测试发现有所提升，但是提升的不是很明显（也可以说很明晰），也可能和无线网和腾讯云轻量云晚上的宽带有影响，使用此种方法，可以减少磁盘的读写，更加快速的读取信息。
