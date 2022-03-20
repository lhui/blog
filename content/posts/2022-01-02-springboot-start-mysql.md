---
title: '[SpringBoot 指南] 连接 mysql 数据库并进行增删改查测试'
author: Li Hui
type: post
date: 2022-01-02T15:56:05+00:00
url: /springboot-start-mysql.html
views:
  - 355
bot_views:
  - 759
categories:
  - 技术
tags:
  - Springboot

---
落库是软件开发中的重要的事情，软件接受完成请求后，对请求的结果进行落入输入库是一件很重要的事情，而本篇文章想写出的内容就是 Springboot 连接本地的数据库的使用方案，本章文章也是入门的文章，因此篇幅可能不大。

本篇文章的主要内容有哪些呢？ 连接数据库主要分为

  1. 启动数据库
  2. 设置依赖
  3. 连接数据库并测试 增删改查基本功能

因此文章分为下面的三部分

## 1. 启动数据库

本文章为了演示比较简便采用的是 docker 创建的数据库

Docker 安装很容易安装，此处不再赘述 Docker 命令如何使用将单独写出 本文章只涉及几个日常命令 `docker run` , `docker ps`

命令如下:

<pre><code class="language-bash line-numbers">docker run --platform=linux/x86_64 -p 13306:3306 -e MYSQL_ROOT_PASSWORD=test --name test -d mysql:5.7
</code></pre>

命令释义：

<pre><code class="language-bash line-numbers">--platform 设置平台的类型
-p {宿主机端口}:{容器端口}
-e 设置变量
--name 设置容器的名称
-d 后台运行
</code></pre>

使用 `docker ps` 查看容器状态

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221342.png)

使用数据库连接工具连接数据库，并创建数据库 `person` 和数据表 `person`

建表语句

<pre><code class="language-sql line-numbers">create table person
(
    id   bigint(100) auto_increment
        primary key,
    name varchar(256) null,
    constraint person_id_uindex
        unique (id)
);

</code></pre>

## 2. 添加依赖并设置连接信息

### 2.1 添加依赖

在 `build.gradle` 中添加如下依赖

本文采用的是最新的依赖，如果企业使用，推荐使用稳定版本

<pre><code class="language-yaml line-numbers">    implementation 'org.springframework.data:spring-data-jpa:2.6.0'
    implementation 'mysql:mysql-connector-java:8.0.25'
    implementation 'org.projectlombok:lombok:1.18.20' # 为了快速开发
</code></pre>

所在位置如下:


![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221427.png)

点击右上角小象标志刷新依赖

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221504.png)

### 2.2 配置连接信息

在 resources 目录下添加 `application.yml` 文件并添加如下配置

<pre><code class="language-yaml line-numbers">spring:
  datasource:
    url: jdbc:mysql://localhost:13306/person
    username: root
    password: test
</code></pre>

## 3. 测试连接数据库并测试业务逻辑

### 3.1 查询数据库测试

代码依次如下:

`Person.java`

<pre><code class="language-java line-numbers">package com.example.firstapi;

import lombok.Data;

import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Data
@Entity
@Table(name = "person")
public class Person {
    @Id
    private long id;
    private String name;
}

</code></pre>

`PersonRepository.java`

<pre><code class="language-java line-numbers">package com.example.firstapi;

import org.springframework.data.jpa.repository.JpaRepository;

public interface PersonRepository extends JpaRepository&lt;Person, Long&gt; {
}

</code></pre>

`PersonService.java`

<pre><code class="language-java line-numbers">package com.example.firstapi;

import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class PersonService {
    private final PersonRepository personRepository;

    public PersonService(PersonRepository personRepository) {
        this.personRepository = personRepository;
    }

    public List&lt;Person&gt; getAllPerson() {
        return personRepository.findAll();
    }
}

</code></pre>

`PersonController.java`

<pre><code class="language-java line-numbers">package com.example.firstapi;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class PersonController {
    private final PersonService personService;

    public PersonController(PersonService personService) {
        this.personService = personService;
    }

    @GetMapping("/persons")
    public List&lt;Person&gt; GetAllPerson() {
        return personService.getAllPerson();
    }
}

</code></pre>

### 3.2 测试联通

#### 3.2.1 启动时检测

![](https://zimeiti-1253731526.cos.ap-beijing.myqcloud.com/img/20220320221528.png)

#### 3.2.2 代码检测

<pre><code class="language-bash line-numbers">curl --location --request GET '127.0.0.1:9090/person'
</code></pre>

可以看到是返回空数组

我们在数据库中插入数据

SQL 如下：

<pre><code class="language-sql line-numbers">INSERT INTO person.person (name)
VALUES ('xiaoming');

INSERT INTO person.person (name)
VALUES ('xiaohong');

</code></pre>

再次请求

<pre><code class="language-bash line-numbers">curl --location --request GET '127.0.0.1:9090/person'
</code></pre>