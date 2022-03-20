---
title: '[技术书籍]JSON必知必会'
author: Li Hui
type: post
date: 2021-01-12T15:59:34+00:00
url: /book-intoduction-to-json.html
views:
  - 2417
bot_views:
  - 929
love:
  - 2
categories:
  - 读书
tags:
  - JSON
  - 技术书籍
  - 读书笔记

---
![image-20210113000350956][1]

# 引言

2021年1月12号 看完了 2021年的第一本书, 也是第一本技术书籍, 这本书挺简单的, 没有记录花了多长时间读完, 也就是2-3个小时吧, 11号晚上和12号晚上两个晚上读完的 对了 写这篇文章的时候 是2021-01-12 22:24.

简短的总结一下这篇文章: "这本书介绍了 JSON是什么,可以用JSON做什么和那些别有用心的人会用它做什么"

JSON是什么: JSON全称为 JavaScript Object Notation(JavaScript 对象表示法),虽然带有JavaScript的字样,但是和JavaScript并没有强绑定,JSON是一种信息的表示法,只不过其中的类型定义有借鉴JavaScript的地方. 简而言之 JSON是一种数据的表示方法,一般用来传输交互数据,保存配置文件等.

可以用JSON做什么: JSON一般使用来用于传输数据和保存配置信息.

别有用心的人会拿来做什么: 其实这一点也是我们进行安全防范的地方, 本书中讲述的主要是和数据传输相关的跨站请求伪造CSRF(cross-site request forgery，读作sea-surf) [利用新人机制进行攻击] 和注入攻击(通过像网站注入恶意代码来实现) 比如苦熬站脚本攻击(Cross-site scripting,XSS) 在使用JSON 时常见的安全漏洞通常发生在JavaScript 从服务器获取到一段JSON字符串并将其转化为JavaScript 对象时。此时如果将相应转换后的代码装载到内存中,再运行,将会产生一项不到的麻烦,毕竟谁都不知道被修改过的数据是好还是坏.

# 本书的主要内容

## 什么是JSON

JSON是一种数据交换格式,JSON独立于编程语言,JSON基于JavaScript对象字面量**表示法**,JSON表达数据的方式对通用的编程概念都很友好.

表示法是指一个用于表示诸如数字或单词等数据的字符系统,比如用象形文字表示数量和什么动物

## JSON的格式

这个是重点 JSON是什么格式的,什么格式正确,什么格式重要很重要. 首先JSON是**键值对(key-value)**, 且键值对的键需要用""引起来,值可以遵循数据类型的形式,比

JSON的键(key)中的""中可以包括 ' (单引号)比如 `"Lindsay's anmail":"cat"` 便是合法的, 可以使用的扩展名 `.json`

如下面的示例

### 鞋子的示例

从上大小依次是 字符串, 字符串, 数值型, 布尔型

<pre><code class="language-json line-numbers">{
    "brand": "Crocs",
    "color": "pink",
    "size": 9,
    "hasLaces": false
}
</code></pre>

书中提到了一个比较简单解释JSON中开始结束的示例如下:

• {（左花括号）指“开始读取对象”  
• }（右花括号）指“结束读取对象”  
• [（左方括号）指“开始读取数组”  
• ]（右方括号）指“结束读取数组”  
• :（冒号）指“在名称- 值对中分隔名称和值”  
• ,（逗号）指“分隔对象中的名称- 值对”或者“分隔数组中的值”；也  
可以认为是“一个新部分的开始”

### JSON和JavaScript对象

JSON

<pre><code class="language-json line-numbers">{
  "title" : "This is my title.",
  "body" : "This is the body."
}
</code></pre>

JavaScript对象

<pre><code class="language-json line-numbers">{
  title : "This is my title.",
  body : "This is the body."
}
</code></pre>

错误的形式1

<pre><code class="language-json line-numbers">{
  'title ': "This is my title.",
  'body' : "This is the body."
}
</code></pre>

错误的形式2

<pre><code class="language-json line-numbers">{
  "title" = "This is my title.",
  "body"  = "This is the body."
}
</code></pre>

### JSON的媒体类型

媒体类型也是数据传输的时候的格式要求, 比如提前告知接收方这次发送的是什么类型的数据, 还有其他的名称如"互联网媒体类型","内容类型",或者"MIME类型" 其采用 "类型/子类型"的格式表示,JSON的MIME类型是: `application/json` 类型的MIME类型还有最常见的`text/html` 就是传输网页时的格式, 比如访问Google时,打开F12监控网络,就会看到如下的返回结果

![image-20210112230649040][2] 

## JSON的数据类型

主要包括 数字(整型,浮点数,定点数),字符串(如"a","A"和"apple") 布尔类型 对象 null 与数组

### 对象类型

这个和对象是一一对应的看下面的形式即可理解

<pre><code class="language-json line-numbers">{
    "person": {
        "name": "Lindsay Bassett",
        "heightInInches": 66,
        "head": {
            "hair": {
                "color": "light blond",
                "length": "short",
                "style": "A-line"
                    },
                "eyes": "green"
                }
                }
}
</code></pre>

### 字符串类型

<pre><code class="language-json line-numbers">{ "animal" : "cat" }
</code></pre>

特殊字符需要转义

• `\"` (双引号)  
• `\\` (反斜线)  
• `\/`（正斜线）  
• `\b`（退格符）  
• `\f`（换页符）  
• `\t`（制表符）  
• `\n`（换行符）  
• `\r`（回车符）  
• `\u` 后面跟十六进制字符（如笑脸表情\u263A）

**转义前**:

<pre><code class="language-json line-numbers">{
"story": "\t Once upon a time, in a far away land \n there lived a princess."
}
</code></pre>

**转义后**:

<pre><code class="language-json line-numbers">{
"story": "\\t Once upon a time, in a far away land \\n there lived a princess."
}
</code></pre>

### 数字类型

<pre><code class="language-json line-numbers">{
"widgetInventory": 289,
"sadSavingsAccount": 22.59,
"seattleLatitude": 47.606209,
"seattleLongitude": -122.332071,
"earthsMass": 5.97219e+24
}
</code></pre>

### 布尔类型

**true和false仅为小写**

<pre><code class="language-json line-numbers">{
"toastWithBreakfast": false,
"breadWithLunch": true
}
</code></pre>

### null类型

这种类型表明没有就是没有,比如手上表的颜色,如果没有表的话就不会有表的颜色

<pre><code class="language-json line-numbers">{
"freckleCount": 1,
"hairy": false,
"watchColor": null
}
</code></pre>

### 数组类型

<pre><code class="language-json line-numbers">{
"eggCarton": [
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg",
"egg"
]
}
</code></pre>

## 一致性校验(JSON Schema)

验证是很有必要的,比如需要拒听规定数据类型,是否包含需要的数据,值的形式是不是需要的(比如指定范围,最大最小等)

第一个键值对 声明的名称为"$schema" 值必须是所用的草案的版本的链接 比如下面的示例

<pre><code class="language-json line-numbers">{
"$schema": "http://json-schema.org/draft-04/schema#"
}
</code></pre>

第二个键值对应该是JSON Schema的标题

<pre><code class="language-json line-numbers">{
"$schema": "http://json-schema.org/draft-04/schema#",
"title": "Cat"
}
</code></pre>

第三个键值对为属性

<pre><code class="language-json line-numbers">{
"$schema": "http://json-schema.org/draft-04/schema#",
"title": "Cat",
"properties": {
        "name": {
             "type": "string"
                },
        "age": {
            "type": "number",
            "description": "Your cat's age in years."
            },
        "declawed": {
            "type": "boolean"
                    }
            }
}
</code></pre>

接下来就可以验证了

比如对下述的数据做验证

<pre><code class="language-json line-numbers">{
"name": "Fluffy",
"age": 2,
"declawed": false
}
</code></pre>

显然类型 符合 可以通过

### 定义必填字段

再加入第四个键值对 值为数组

键为 "required"值为属性(properties)的键(key)

<pre><code class="language-json line-numbers">{
    "$schema":"http://json-schema.org/draft-04/schema#",
    "title":"Cat",
    "properties":{
        "name":{
            "type":"string"
        },
        "age":{
            "type":"number",
            "description":"Your cat's age in years."
        },
        "declawed":{
            "type":"boolean"
        },
        "description":{
            "type":"string"
        }
    },
    "required":[
        "name",
        "age",
        "declawed"
    ]
}
</code></pre>

合法的JSON

<pre><code class="language-json line-numbers">{
    "name":"Fluffy",
    "age":2,
    "declawed":false
}
</code></pre>

### 定义所需数据要求

比如大小,在属性中的值里面添加 长度( minLength,maxLength),大小范围(minmum) 等等

<pre><code class="language-json line-numbers">{
    "$schema":"http://json-schema.org/draft-04/schema#",
    "title":"Cat",
    "properties":{
        "name":{
            "type":"string",
            "minLength":3,
            "maxLength":20
        },
        "age":{
            "type":"number",
            "description":"Your cat's age in years.",
            "minimum":0
        },
        "declawed":{
            "type":"boolean"
        },
        "description":{
            "type":"string"
        }
    },
    "required":[
        "name",
        "age",
        "declawed"
    ]
}
</code></pre>

JSON Schema主页 （http://json-schema.org/）

JSON Schema 验证规范（http://json-schema.org/latest/json-schema-validation.  
html）

## 其他

###　跨域资源共享（CORS）

非同源地址访问 如果没有标明 浏览器会自动阻拦请求,非同源指的是 域名或者IP ,端口 有一个不同则为不同, 这里一般需要后端协调来解决.

### NoSQL

NoSQL是相对于SQL来说的 SQL(Structured Query Language) 结构性数据库来讲的

SQL 是关系型数据库,其采用表格,行列用结构化形式存储数据,保存相应的数据,有相应的关联关系,比如保存账户信息的白噶尔肯定要与保存着账户地址的摆个存在关联,一般会有一个键,用来区分账户的列,来给两个表建立一种联系

NoSQL 即非关系型数据库 ,非关系型数据库的类型就多了,其中一种是键值对存储的方式,比如采用文档存储的方式,文档类型可以是XML型,JSON型等形式.

此处摘抄https://blog.csdn.net/weixin_44259720/article/details/104839050的表格来展示不同的NoSQL类型

|  分类   |                                                                                                                                 相关产品                                                                                                                                 |                应用场景                 |              数据模型              |                                                                         优点                                                                          |                缺点                 |
|:-----:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------:|:------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------:|
| 键值数据库 | <a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/redis/" target="_blank"  rel="nofollow" >Redis</a>、<a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/view/6574.html" target="_blank"  rel="nofollow" >Memcached</a>、Riak | 内容缓存，如会话、配置文件、参数等； 频繁读写、拥有简单数据模型的应用 |    <key,value> 键值对，通过散列表来实现    |                                                                 扩展性好，灵活性好，大量操作时性能高                                                                  | 数据无结构化，通常只被当做字符串或者二进制数据，只能通过键来查询值 |
| 列族数据库 |                                                             Bigtable、<a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/hbase/" target="_blank"  rel="nofollow" >HBase</a>、Cassandra                                                             |             分布式数据存储与管理              |       以列族式存储，将同一列数据存在一起        |                                                                  可扩展性强，查找速度快，复杂性低                                                                   |          功能局限，不支持事务的强一致性          |
| 文档数据库 |                                                                <a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/mongodb/" target="_blank"  rel="nofollow" >MongoDB</a>、CouchDB                                                                 |       Web 应用，存储面向文档或类似半结构化的数据       | <key,value> value 是 JSON 结构的文档 | <a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/data_structure/" target="_blank"  rel="nofollow" >数据结构</a>灵活，可以根据 value 构建索引 |             缺乏统一查询语法              |
| 图形数据库 |                                                              <a class="wp-editor-md-post-content-link" href="http://c.biancheng.net/view/6579.html" target="_blank"  rel="nofollow" >Neo4j</a>、InfoGrid                                                              |         社交网络、推荐系统，专注构建关系图谱          |              图结构               |                                                                      支持复杂的图形算法                                                                      |         复杂性高，只能支持一定的数据规模          |

比如CouchDB数据库采用的就是JSON文档的存储方式.

问题来了 如果我们采用NoSQL如何提取出需要筛选的数据呢? 这里需要用到的就是视图了,在使用NoSQL查询的时候应该会有这部分的内容.

### 序列化与序列化

序列化可以等同于编码(encode),即把原数据(比如对象格式等)保存为JSON的格式,而反序列化就是将JSON数据转化为对象格式.

### 还有什么其他的作用吗

还有的,比如保存配置文件,形式一般是`.json` 格式, 来保存应用的配置信息, 以保证下一次的读取.当然保存数据的格式还是有INI格式 XML格式,各有所长,不过现在使用面比较广,比价多的是JSON格式.

# 参考资料

  1. JSON必知必会 [美] Lindsay Bassett著 魏嘉汛译
  2. https://blog.csdn.net/weixin_44259720/article/details/104839050

 [1]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210113000350956.png
 [2]: https://image-cdn-1253731526.cos.ap-beijing.myqcloud.com/img/image-20210112230649040.png