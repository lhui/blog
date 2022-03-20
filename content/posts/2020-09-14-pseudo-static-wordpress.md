---
title: '[博客优化]为Wordpress加入伪静态'
author: Li Hui
type: post
date: 2020-09-14T12:07:16+00:00
url: /pseudo-static-wordpress.html
views:
  - 781
bot_views:
  - 1622
categories:
  - 博客优化
tags:
  - 博客优化

---
# 前言

为什么要加入伪静态呢，是Wordpress的网址不好看吗，嗯。。。。确实是不好看，而且网址之间还是不连续的，我都看傻了<a href="http://lihui.net/?p=23" target="_blank"  rel="nofollow" >http://lihui.net/?p=23</a> 这种网址 都猜不出写了啥...

加入伪静态的优点有哪些呢？

首先来说 在一定意义上来讲，搜索引擎对于静态的页面的收录的效果要相对来说要好（当然有很多原因，比如网址不易变动，内容固定，访问速度快等等），因此网站做伪静态对于SEO的效果还是很明显的。

第二点 就是上述的问题，网页无法辨识内容，从p=23能看出啥 反正我看不出和文章的主要内容git有任何关系，因此Wordpress伪静态的优点也就将地址进行自定义化

涉及的知识： Nginx 配置 Wordpress配置

# 步骤

其实伪静态在nginx很简单，只需要添加一些代码即可

## 修改配置文件

在配置想要配置的网站的配置文件\***.conf中的网站的位置即server里面加入下面的代码即可

<pre><code class="language-bash">location / {
    if (-f &lt;span class="katex math inline">request_filename/index.html){
        rewrite (.*)&lt;/span>1/index.html break;
    }
    if (-f &lt;span class="katex math inline">request_filename/index.php){
        rewrite (.*)&lt;/span>1/index.php;
    }
    if (!-f $request_filename){
        rewrite (.*) /index.php;
    }
}</code></pre>

## 使得nginx生效

此处也是使用的ngnix的命令 进行安全加载 可以首先进行测试 看配置文件修改的是否正确

<pre><code class="language-bash">ngnix -t # this is the cmd for test the conf file</code></pre>

当出现 \**** test is success 样式的字眼出现时候证明配置修改的是成功的 当出现fail的时候 修改的配置应该是不正确的。

下面的为执行命令

<pre><code class="language-bash">ngnix -s reload # reload the conf</code></pre>

此时ngnix 已经生效 伪静态的服务器端已经配置完成

## Wordpress端的配置

Wordpress端的配置相对来说比较简单，直接找到设置，在从中找到固定链接，进行修改，如下图所示

![puXEHz][1] 

我采用的修改为下图所示

![aSE4gx][2] 

点击保存更改就已经修改成功，此时最好打开一个新的页面（此页面先不关闭），进行测试时候已经修改为伪静态（即上述的形式），如果出现问题，尽快修改回第一个，减少网站的不可访问时间。

# 思考

有时候，知识觉得问题很复杂，尝试过后才发现也就那个样子，差不多的。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/puXEHz.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/aSE4gx.png