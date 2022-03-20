---
title: Docker基础命令
author: Li Hui
type: post
date: 2021-01-13T15:57:45+00:00
url: /docker-base-command.html
views:
  - 2745
bot_views:
  - 1862
love:
  - 2
categories:
  - Docker
tags:
  - Docker

---
![image-20210113235714155][1]

# 前言

随着容器化技术的推广,在不久的将来,大多数的公司都将采用容器化技术对现有的业务进行改造,因此容器化是一个大趋势, 在当下, 正值云原生的发展的前期, 掌握容器化技术, 对于云原生的业务的了解也是一种帮助, 本文主要还是整理一下Docker的基本命令, Docker基本命令其实很好找到, 本文只是对自己的掌握的命令的一个总结和对Docker命令的整理, 以防自己以后会忘记.

本文采用的是<a class="wp-editor-md-post-content-link" href="https://www.docker.com/play-with-docker" target="_blank"  rel="nofollow" >https://www.docker.com/play-with-docker</a> 提供的 每次提供四个小时的试用期, 完全可以满足使用.

# 内容

## 获取镜像(docker pull)

### 命令

image_name是镜像的名称 后面如果没有tag 则默认拉去最新的镜像,如果有则拉去对应Tag号的镜像

<pre><code class="language-bash line-numbers">$  docker pull {{image_name}}:{{tag}}
</code></pre>

### demo

#### 带Tag

<pre><code class="language-bash line-numbers">$ docker pull centos:7
</code></pre>

![image-20210113232024768][2] 

#### 不带Tag

<pre><code class="language-bash line-numbers">$ docker pull centos
</code></pre>

![image-20210113232044202][3] 

## 查看镜像信息

### 命令&&demo

<pre><code class="language-bash line-numbers">$ docker images
</code></pre>

![image-20210113232218482][4] 

## 搜寻镜像

### 命令

<pre><code class="language-bash line-numbers">$ docker search [OPTIONS] TERM
</code></pre>

参数解释

<pre><code class="line-numbers">Options:
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print search using a Go template
      --limit int       Max number of search results (default 25)
      --no-trunc        Don't truncate output
</code></pre>

### demo

<pre><code class="language-bash line-numbers">$ docker search nginx
</code></pre>

![image-20210113233133843][5] 

## 删除镜像

删除一个或者多个镜像 注意删除容器时 docker rm CONTAINER

### 命令

<pre><code class="language-bash line-numbers">$ docker rmi [OPTIONS] IMAGE [IMAGE...]
</code></pre>

参数

<pre><code class="language-bash line-numbers">Options:
  -f, --force      Force removal of the image
      --no-prune   Do not delete untagged parents
</code></pre>

### demo

<pre><code class="language-bash line-numbers">$ docker rmi centos:latest
</code></pre>

![image-20210113233530266][6] 

## 创建镜像

从一个变化的容器种创建一个镜像,为何这样说,因为容器是可写的,而镜像也就是image是只读的.

### 命令

<pre><code class="language-bash line-numbers">$ docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
</code></pre>

参数

<pre><code class="language-bash line-numbers">Options:
  -a, --author string    Author (e.g., "John Hannibal Smith &lt;hannibal@a-team.com&gt;")
  -c, --change list      Apply Dockerfile instruction to the created image
  -m, --message string   Commit message
  -p, --pause            Pause container during commit (default true)
</code></pre>

### demo

<pre><code class="language-bash line-numbers">$ docker commit -m "Added a demo file" -a "dockerUser" d4b6b8a8db0d demoImg:0.0.1
</code></pre>

![image-20210113234321827][7] 

![image-20210113234332658][8] 

## 存入和载入镜像

### 存入镜像

导出镜像为本地tar文档

### 命令

<pre><code class="language-bash line-numbers">$ docker save [OPTIONS] IMAGE [IMAGE...]
</code></pre>

参数

<pre><code class="line-numbers">Options:
  -o, --output string   Write to a file, instead of STDOUT
</code></pre>

### demo

<pre><code class="language-bash line-numbers">$ docker save -o centos.tar centos
</code></pre>

![image-20210113234736875][9] 

### 载入镜像

将导出的tar文件导入到本地镜像仓库中,会导入镜像和其元数据信息

#### 命令

<pre><code class="language-bash line-numbers">$ docker load [OPTIONS]
</code></pre>

参数

<pre><code class="language-bash line-numbers">Options:
  -i, --input string   Read from tar archive file, instead of STDIN
  -q, --quiet          Suppress the load output
</code></pre>

#### demo

<pre><code class="language-bash line-numbers">docker load &lt; centos.jar
</code></pre>

![image-20210113235129588][10]

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113235714155.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113232024768.png
 [3]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113232044202.png
 [4]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113232218482.png
 [5]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113233133843.png
 [6]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113233530266.png
 [7]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113234321827.png
 [8]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113234332658.png
 [9]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113234736875.png
 [10]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113235129588.png