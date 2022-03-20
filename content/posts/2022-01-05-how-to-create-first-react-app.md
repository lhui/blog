---
title: 如何搭建第一个 React 程序
author: Li Hui
type: post
date: 2022-01-05T14:22:22+00:00
url: /how-to-create-first-react-app.html
views:
  - 210
bot_views:
  - 197
categories:
  - 未分类
tags:
  - react

---
最近在公司中的项目中是一个 React native 开发的程序，因此就有了这个文章，搭建第一个 React 的程序。

这个应该会很快写完，毕竟比较简单，这篇文章的目的还是尝试如何创建第一个React程序

学习一个事物，我认为最大限度的降低初学者的成本是最重要的，毕竟创造一个新的软件为了让其他人使用，而不是让做出来的软件自己都不用。  
Mozilla 关于 JSX 语法的描述

`由于 JSX 是 HTML 和 JavaScript 的结合，因此一些开发人员认为它很直观。其他人则说它的混合特性使它变得混乱。但是，一旦熟悉了它，它将使您能够更快，更直观地构建用户界面，并使其他人一眼就能更好地理解您的代码库。`

本文分为下面几个方面 1. 环境预配置, 2. 创建并演示

## 1. 环境预配置

环境预配置采用 NodeJS 环境 详情可以参考 <a class="wp-editor-md-post-content-link" href="https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started#%E8%A6%81%E6%B1%82" target="_blank"  rel="nofollow" >Mozilla 安装 NodeJS 环境配置 </a>

## 2. 创建并演示

安装完成 nodejs 后可以使用下列命令创建项目名称为 `moz-todo-react` 的 React 应用

<pre><code class="language-bash line-numbers">npx create-react-app moz-todo-react
</code></pre>

![][1] 

在刚才的 terminal 中输入以下命令

<pre><code class="language-bash line-numbers">cd moz-todo-react
npm start
</code></pre>

会自动打开地址 http://localhost:3000/ , 效果如下  
![][2] 

未来我们会有新的章节来介绍文章的内容以及如何使用 React 进行软件开发

实践与写作大约使用 40 分钟

遗留问题：

  1. npm vs yarn 有什么不同，日常使用哪一个最好？

参考文章

<a class="wp-editor-md-post-content-link" href="https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started" title="Mozilla React get Start" target="_blank"  rel="nofollow" >https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started</a>

 [1]: https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/react-moz-starter.png
 [2]: https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/first-react.png