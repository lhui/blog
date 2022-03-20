---
title: '[CLI应用学习]时间使用GitHub CLI'
author: Li Hui
type: post
date: 2020-09-21T00:00:21+00:00
url: /learn-gh-cli.html
views:
  - 2353
bot_views:
  - 596
categories:
  - CLI应用
tags:
  - CLI
  - GitHub

---
# 前言

不久前 GitHub发布了自己的CLI应用，不得不多说，在微软收购GitHub迎来的大的进步，近期出现了很多很多的大动作，发布CLI应用，发布移动端的应用等等，虽然不一定和微软有必然关系，不过GitHub最近确实不错。本期主要是学习GitHub CLI 的应用，并分析GitHub CLI的优缺点。

**问题前置： GitHub api 好像不是那么好连接 要想办法的。**

# 内容

首先展示GitHub CLI 的功能 支持整个的工作流（处理issue 拉取请求 check 发行 和更多） 脚本和个性化 商业同样适用 代码开源

![ZXgPoA][1] 

首先我们来进行安装 本次采用MacBook来安装 命令如下：

<pre><code class="language-bash">$ brew install gh</code></pre>

> 此处因为某些原因brew的下载速度不是很理想，可以采用换用清华的源进行调整<a href="https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/" target="_blank"  rel="nofollow" >https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/</a> 其中可能会遇到一些其他的问题 比如brew link gh 显示权限不足 可以 chmod 77 {{提示的路径}} 而后再次运行 brew link gh即可

安装完成后即可以使用

<pre><code class="language-bash">gh</code></pre>

返回结果

<pre><code class="language-bash"></code></pre>

## 使用CLI 登陆

命令行

<pre><code class="language-bash">gh auth login {{token}} #token 获取的方式如下面所示</code></pre>

| 获取的token                           |
| ---------------------------------- |
| 1. 登陆GitHub的网站 设置（setting）-> 开发者-> |

![image-20200920222758765][2] 

![8ARrPY][3] 

![hi3msq][4] 

在此处生成token 然后给予相应的权限（推荐给予部分权限，熟练者可以给予全部权限，权限问题，很严重的呀）

![UC7wfe][5] 

本文示例中 我只给予了token仓库和读组织的的权限（CLI 应用要求的最小的权限），其他的权限都没有给，应该此次使用不会涉及到太多其他方面的问题。

然后点击生成token 因为token只保留一次 记得要保存（安全期间可以不保存，毕竟连你都不知道，其他人更不知道了）

## 进入登陆环节

<pre><code class="language-bash">$ gh auth login</code></pre>

返回结果

![8Im1NS][6] 

此时选择第一个 商业服务器选择第二个

而后开始选择登陆方式[两种 第一种通过浏览器登录 第二种通过 token登陆]，我们前面申请了token 此处使用token登陆。

![OIYtNE][7] 

而后填入自己的token

![2o9WYP][8] 

注意此处最小的权限是repo和读取组织权限

此后是通过何种方式进行连接（我个人比较倾向于ssh连接方式）

![SwiKa1][9] 

此时连接建立完成✅

整体流程如下图所示

![qyu7f0][10] 

我们可以发现 这个登陆的流程相对来说比较简单 此时账号已经登陆上去了。

## 指令表格

因为GitHub是和Git仓库是相连的，因此需要在Git仓库中使用（且仓库链接到远程的GitHub）

GH命令官网 <a href="https://cli.github.com/manual/" target="_blank"  rel="nofollow" >https://cli.github.com/manual/</a>

全部命令如下表

| 一级指令                                                                                                  | 二级指令                                                                                                      |
| ----------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| <a href="https://cli.github.com/manual/gh_alias" target="_blank"  rel="nofollow" >alias</a>           |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_alias_delete" target="_blank"  rel="nofollow" >delete</a>       |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_alias_list" target="_blank"  rel="nofollow" >list</a>           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_alias_set" target="_blank"  rel="nofollow" >set</a>             |
| <a href="https://cli.github.com/manual/gh_api" target="_blank"  rel="nofollow" >api</a>               |                                                                                                           |
| <a href="https://cli.github.com/manual/gh_auth" target="_blank"  rel="nofollow" >auth</a>             |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_auth_login" target="_blank"  rel="nofollow" >login</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_auth_logout" target="_blank"  rel="nofollow" >logout</a>        |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_auth_refresh" target="_blank"  rel="nofollow" >refresh</a>      |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_auth_status" target="_blank"  rel="nofollow" >status</a>        |
| <a href="https://cli.github.com/manual/gh_completion" target="_blank"  rel="nofollow" >completion</a> |                                                                                                           |
| <a href="https://cli.github.com/manual/gh_config" target="_blank"  rel="nofollow" >config</a>         |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_config_get" target="_blank"  rel="nofollow" >get</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_config_set" target="_blank"  rel="nofollow" >set</a>            |
| <a href="https://cli.github.com/manual/gh_gist" target="_blank"  rel="nofollow" >gist</a>             |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_gist_create" target="_blank"  rel="nofollow" >create</a>        |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_gist_edit" target="_blank"  rel="nofollow" >edit</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_gist_list" target="_blank"  rel="nofollow" >list</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_gist_view" target="_blank"  rel="nofollow" >view</a>            |
| <a href="https://cli.github.com/manual/gh_issue" target="_blank"  rel="nofollow" >issue</a>           |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_close" target="_blank"  rel="nofollow" >close</a>         |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_create" target="_blank"  rel="nofollow" >create</a>       |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_list" target="_blank"  rel="nofollow" >list</a>           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_reopen" target="_blank"  rel="nofollow" >reopen</a>       |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_status" target="_blank"  rel="nofollow" >status</a>       |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_issue_view" target="_blank"  rel="nofollow" >view</a>           |
| <a href="https://cli.github.com/manual/gh_pr" target="_blank"  rel="nofollow" >pr</a>                 |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_checkout" target="_blank"  rel="nofollow" >checkout</a>      |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_checks" target="_blank"  rel="nofollow" >checks</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_close" target="_blank"  rel="nofollow" >close</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_create" target="_blank"  rel="nofollow" >create</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_diff" target="_blank"  rel="nofollow" >diff</a>              |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_list" target="_blank"  rel="nofollow" >list</a>              |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_merge" target="_blank"  rel="nofollow" >merge</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_ready" target="_blank"  rel="nofollow" >ready</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_reopen" target="_blank"  rel="nofollow" >reopen</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_review" target="_blank"  rel="nofollow" >review</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_status" target="_blank"  rel="nofollow" >status</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_pr_view" target="_blank"  rel="nofollow" >view</a>              |
| <a href="https://cli.github.com/manual/gh_release" target="_blank"  rel="nofollow" >release</a>       |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_create" target="_blank"  rel="nofollow" >create</a>     |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_delete" target="_blank"  rel="nofollow" >delete</a>     |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_download" target="_blank"  rel="nofollow" >download</a> |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_list" target="_blank"  rel="nofollow" >list</a>         |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_upload" target="_blank"  rel="nofollow" >upload</a>     |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_release_view" target="_blank"  rel="nofollow" >view</a>         |
| <a href="https://cli.github.com/manual/gh_repo" target="_blank"  rel="nofollow" >repo</a>             |                                                                                                           |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_repo_clone" target="_blank"  rel="nofollow" >clone</a>          |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_repo_create" target="_blank"  rel="nofollow" >create</a>        |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_repo_fork" target="_blank"  rel="nofollow" >fork</a>            |
|                                                                                                       | <a href="https://cli.github.com/manual/gh_repo_view" target="_blank"  rel="nofollow" >view</a>            |

## 简单演示

因为指令相对来说较多 只使用其中几个演示。

## 显示GitHub仓库信息

切换到连接到GitHub的仓库，使用下面的命令行

命令行

<pre><code class="language-bash">$ gh repo view</code></pre>

返回结果

![eqYJm5][11] 

## 显示issue

同样在上述的仓库 使用下面的命令行

<pre><code class="language-bash">$ gh issue list</code></pre>

返回结果

![M3AAGQ][12] 

# 总结

优点： 可以使用命令行操作GitHub的内容，比较的简单，比较快速就可以使用，较为友好。

缺点： 当前应用还存在一些问题 例如 gh release create 在使用brew安装的时候无法使用。显示只有这些指令（ alias api auth completion config gist help issue pr repo）可以使用。

总体感觉还是不错的，希望GitHub可以将这个应用越做越好。

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/ZXgPoA.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/image-20200920222758765.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/8ARrPY.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/hi3msq.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/UC7wfe.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/8Im1NS.png
 [7]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/OIYtNE.png
 [8]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/2o9WYP.png
 [9]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/SwiKa1.png
 [10]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/qyu7f0.png
 [11]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/eqYJm5.png
 [12]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/M3AAGQ.png