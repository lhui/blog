---
title: 如何使用 gitbook cli工具
author: Li Hui
type: post
date: 2022-01-09T15:43:27+00:00
url: /how-to-use-gitbook.html
bot_views:
  - 363343
views:
  - 4331
love:
  - 1
categories:
  - Git系列
tags:
  - gitbook

---
gitbook 是一个极好的工具帮助我们来写一个富有逻辑性的书籍。使用 gitbook cli 可以轻松地帮助我们非写作化的进程，使得我们更加专注于写作本身。

关于 gitbook cli 工具其实写作的内容并不多主要涉及的是两个方面，第一个是对应的 node 版本要选择正确，此步骤可以采用 node 版本控制工具 nvm 解决， 第二个就是 gitbook cli 工具的使用方法。

## 1. 安装 nvm node 版本管理工具

### 1.1 安装 nvm

安装方式可以参考官方链接 <a class="wp-editor-md-post-content-link" href="https://github.com/nvm-sh/nvm#install--update-script" target="_blank"  rel="nofollow" >https://github.com/nvm-sh/nvm#install--update-script</a>

此篇文章的安装版本可能已经过时 本文书写时间 2022-01-09 如果距离过长，请直接找到上述网站安装

<pre><code class="language-bash line-numbers">curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
</code></pre>

\`\`

### 1.2 下载 node 10 并使用 node 10

这里的命令也比较简单

<pre><code class="language-bash line-numbers">nvm install 10
nvm use 10
</code></pre>

此时 terminal 中就是 10 的版本， 我们下面开始安装 gitbook cli 应用

## 2. 安装 gitbook cli 工具并使用

### 2.1 安装

<pre><code class="language-bash line-numbers">npm install -g gitbook-cli
</code></pre>

此时 gitbook cli 工具已经全局安装好了

## 2.2 使用

<pre><code class="language-bash line-numbers">gitbook init demo-book
</code></pre>

此时 gitbook cli 就已经创建好，至于具体文件含义，我找到了一个更具体的文档，列在下方，直接看下面的文档更好理解如何使用。

<a class="wp-editor-md-post-content-link" href="https://chrisniael.gitbooks.io/gitbook-documentation/content/" target="_blank"  rel="nofollow" >https://chrisniael.gitbooks.io/gitbook-documentation/content/</a>