---
title: React 组件示例
author: Li Hui
type: post
date: 2022-01-06T15:13:02+00:00
url: /create-react-component.html
views:
  - 219
bot_views:
  - 292
categories:
  - 未分类
tags:
  - react

---
上一节，我们使用 create-react-app 生成示例程序的代码，这一节我们详细介绍下如何进行修改代码

看了一些 React 的书籍，其实 React 使用 JSX 语法，将程序的模块化和抽象做的很好。

我们新建立的程序的目录如下

<pre><code class="language-bash line-numbers">moz-todo-react
├── README.md
├── node_modules
├── package.json
├── package-lock.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── reportWebVitals.js
    └── setupTests.js
</code></pre>

关于目录结构的表述我这里直接引用 Mozilla 的描述

目录 **`src`** 是我们花费时间最多的地方，因为它是我们 React 应用源码存放的目录。

目录 **`public`** 包含了开发应用时浏览器会读取的文件，其中最重要的就是 `index.html`。React 将目录 **`src`** 中的代码嵌入这个文件，从而浏览器才能运行此文件。 `index.html` 中的有些内容关乎 create-react-app 的运作，因此除非你知道自己在做什么样的修改，否则不建议编辑这个文件。当然，你可以修改 `index.html` 中的 <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title" target="_blank"  rel="nofollow" >

<title>
  </a> 元素的内容来表现此应用程序通俗易懂的名称。</p> 
  
  <p>
    package.json 与 react 工程并无直接关联，这个是 node modules 的管理的文件。其他的 node 版本管理的软件都会有这个文件。
  </p>
  
  <p>
    React 中最小的就是组件，那何为组件呢，组件的大小如何界定呢？
  </p>
  
  <h2>
    何为组件
  </h2>
  
  <p>
    组件是组成应用程序的最小单元，使用组件可以大大减轻软件开发的工作，提高软件开发的效率，一般组件是实现单一功能的
  </p>
  
  <p>
    下面以《深入 React 技术栈》中的例子为例讲述组件元素的构建
  </p>
  
  <p>
    下面是一个带有 <code>btn btn-blue</code> 的按钮，且其中有 em 元素,且其中有字符串 Confirm
  </p>
  
  <pre><code class="language-bash line-numbers">&lt;button class="btn btn-blue"&gt;
 &lt;em&gt;Confirm&lt;/em&gt;
&lt;/button&gt;
</code></pre>
  
  <p>
    若转移为 Json 对象如下
  </p>
  
  <pre><code class="language-js line-numbers">{
    type: 'button',
    props: {
        className: 'btn btn-blue',
        children: [{
            type: 'em',
            props: {
                children: 'Confirm'
            }
        }]
    }
}
</code></pre>
  
  <p>
    转移为组件元素封装
  </p>
  
  <pre><code class="language-js line-numbers">const Button = ({color,text}) =&gt;{
    return {
        type: 'button',
        props: {
            className: `btn btn - $ {
                color
            }`,
            children: {
                type: 'em',
                props: {
                    children: text,
                },
            },
        },
    };
}
</code></pre>
  
  <p>
    由此我们就有了第一个组件 <code>Button</code>
  </p>
  
  <p>
    参考
  </p>
  
  <ol>
    <li>
      <a class="wp-editor-md-post-content-link" href="https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started" title="Mozilla" target="_blank"  rel="nofollow" >https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started</a>
    </li>
    <li>
      《深入 React 技术栈》
    </li>
  </ol>