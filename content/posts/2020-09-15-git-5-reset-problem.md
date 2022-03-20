---
title: '[Git教程系列]基础教程5 解决修改错分支的问题'
author: Li Hui
type: post
date: 2020-09-15T14:02:14+00:00
url: /git-5-reset-problem.html
views:
  - 640
bot_views:
  - 1457
categories:
  - Git系列
tags:
  - Git系列

---
# 前言

千辛万苦修改完成了代码，当要提交的时候或者提交后，才发现代码写错了分支，直接在master分支做了修改，哎，千辛万苦写的代码不能扔啊，咋办，下面记录一下我修改的过程。

# 步骤

## 如果没有提交(commit)

之所以将这个提到前面，是因为很多情况下，我们都会在写代码的时候忘情的写代码，提价的时候（尤其是使用工具的时候，会不自觉的看一下相应的分支，也有可能是bash的提醒）

此时 有三个步骤 将修改的代码放入stash区 切换分支 从stash中取出来，这时候使用stash和使用栈类似

问题最初的情况 （不巧的是在master分支对hello.txt进行了修改）

![vkUoZu][1] 

直接将所有代码一次写上吧

<pre><code class="language-bash">git stash # 将代码放入相应的缓存区
git chekout dev # 切换到自己所想修改的分支
git stash pop # 将修改的代码从缓存区取出来</code></pre>

返回结果 此时我们已经将修改的结果 转移到了dev分支

![VqYkjj][2] 

## 如果已经进行了提交commit

此时需要多一个步骤 需要回退到上一个分支(或者需要回退到指定的分支)

回退到上个commit

<pre><code class="language-bash">git reset HEAD^</code></pre>

回退到指定分支

<pre><code class="language-bash">git reset 记录唯一值</code></pre>

其他的和上面的一致

操作如下图所示

![7ahXMB][3] 

![2lVDhe][4] 

![swCQNO][5] 

![0dAzF3][6] 

## 已经提交到远程仓库（github/gitlab etc）

Emm.. 这个也有两种情况，无私人信息和有私人信息，尤其是把个人的私钥上传了，如果不撤回来的话，那后果好像很严重的。

### 无私人信息

此种情况还比较好，不影响大碍，可以进行反向提交，将上一次的代码如何提交的如何删除即可

<pre><code class="language-bash">git revert HEAD</code></pre>

此时本地多了一条commit 将上次的提交内容进行反向提交 即增加了一条删除的commit信息

此时在提交至远程即可

<pre><code class="language-bash">git push origin master</code></pre>

### 有私人信息

此种情况非常非常糟糕，一旦被其他人所使用，后果不堪设想。(如果此篇文章有幸被你看到一定要注意)

<pre><code class="language-bash">git reset --hard {{commitid}} # 强制回退到指定分支
git push -f # 强制推送分支（因为线上版本比当前的版本新（多一个新分支））</code></pre>

![GOC0qD][7] 

![ffLDgk][8] 

![Sav8WC][9] 

![58PEfw][10] 

# 总结

通过上面的步骤，我们可以将各种情况的git信息进行修改，如果有不全面的，欢迎进行留言。

参考文章：

  1. [<a href="https://gorden5566.com/post/1010.html" target="_blank"  rel="nofollow" >https://gorden5566.com/post/1010.html</a>](

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/vkUoZu.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/VqYkjj.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/7ahXMB.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/2lVDhe.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/swCQNO.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/0dAzF3.png
 [7]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/GOC0qD.png
 [8]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/ffLDgk.png
 [9]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/Sav8WC.png
 [10]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/Pic/58PEfw.png