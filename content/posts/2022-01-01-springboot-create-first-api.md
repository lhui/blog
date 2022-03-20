---
title: '[SpringBoot 指南] 如何开始 Springboot 之旅 实现自己第一个接口'
author: Li Hui
type: post
date: 2022-01-01T15:29:12+00:00
url: /springboot-create-first-api.html
views:
  - 212
bot_views:
  - 359
categories:
  - 未分类
tags:
  - Springboot

---
书写时间 39m59s

预计发布时间 2022-01-01

这篇文章是 springboot 系列的第一篇文章，如何从零开始学习 Springboot.

我认为学习技术，追寻技术的本质没有任何问题，但是在上手技术的时候可能不需要了解太多的技术细节，首先了解如何使用，而后再想办法如何优化也不乏为一条快速学习和实践的道路。

本篇文章的主要思路是，通过实践最简单的 springboot 的项目，实现我们的第一个接口来叩响 Springboot 学习之门。

本章节分为两个部分 新建项目 和 书写第一个接口

## 新建项目

本篇文章采用 IDEA 创建 springboot 项目, IDEA 开发 Spring 项目有很多的优点，比如代码补全，代码优化，环境内置，还有很多的插件系统，可以大幅度地提高效率，推荐使用 IDEA 进行开发

### 1. 打开 IDEA 新建项目

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221554.png)

### 2. 选择建立 Springboot 项目并填写项目信息

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221622.png)

其中英文名称释义

Name: 项目名称

Location 代码位置

Type: 这里指的是项目的构建方式 选择 Maven 和 Gradle 在初期体验不到不同，此处我选择的是 Gradle

Group: 可以理解为项目组的名称，一般为域名的反写 比如域名是 exmaple.com 则 Group 的数值为 com.example

Project SDK: 这个很好理解 这个是软件开发的环境

Packaging : 打包的方式， Jar 与 War 的区别是 Jar 打包了运行环境， 直接 `java -jar project.jar` 可以启动，而 war 需要放在容器（比如 tomcat）中才可以使用

### 3. 选择依赖

因为我们实现的功能比较简单 我们选择依赖的时候只选择 SpringWeb 即可实现

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221651.png)

注意上面的 Springboot: 后的 2.6.2 这个是 Springboot 的版本号， 其他的依赖会依赖这个号进行兼容性关联，这里我们也不需要关心，点击完成即可进行下一步

### 4. 等待依赖下载完成 运行项目测试项目可以正常运行

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221734.png)

等待箭头所示位置的进度条完成后，点击下图的按钮进行测试

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221804.png)

当出现下图的信息 即代表运行成功 `Started FirstApiApplication in 1.793 seconds (JVM running for 2.42)`

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221843.png)

我们可以从日志中看到 `Tomcat started on port(s): 8080 (http) with context path ''`

程序运行在 8080 端口 我们现在打开浏览器测试 8080 端口 预期结果如下（因为我们并没有设置 匹配 `/` 的路由信息，报如下的错误）


![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221925.png)

我们下面来实现第一个接口

## 实现第一个接口

### 1. 新建文件

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221949.png)

并输入名称，回车确认创建文件

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320222017.png)

第一个接口代码如下

<pre><code class="language-sql line-numbers">package com.example.firstapi;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/hello")
    public String sendHello() {
        return "Hello World";
    }
}
</code></pre>

IDEA 中的界面如下


![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320222102.png)

点击重新运行按钮 进行重新运行项目 测试我们第一个接口是否成功

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320222125.png)

### 2. 测试新接口

访问 <a class="wp-editor-md-post-content-link" href="http://localhost:8080/hello" target="_blank"  rel="nofollow" >http://localhost:8080/hello</a> 我们可以发现 我们所写的代码运行成功

此处的 `GetMapping` 指的是从匹配 HTTP Get 请求的注解，代表当匹配到括号里面到内容时候，采用下面的方法来处理。

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320222140.png)

由此，我们的 Springboot 指南开始正式入门。
