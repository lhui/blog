---
title: React JSX语法再实践
author: Li Hui
type: post
date: 2022-01-07T14:41:37+00:00
url: /react-jsx-re-action.html
views:
  - 261
bot_views:
  - 857
categories:
  - 未分类
tags:
  - react

---
我们上一节封装了一个按钮，这一节我们继续理解封装的概念和了解封装组件需要注意的事项

首先我们回顾上一篇最后的代码，代码如下

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

我们最终调用的形式如下所示 Button({color:'blue', text:'Confirm'}) 进行创建，其实我们发现 `Button` 和 `button` 或者和 `em` 一样都可以 作为一个元素存在，我们可以以 Button 为基础创建特定属性的按钮，将其称为自定义类型的元素 或者可以称为组件元素。和上一节相同，我们可以采用 JSON 结构来描述它

<pre><code class="language-js line-numbers">{
 type: Button,
 props: {
  color: 'blue',
  children: 'Confirm'
 }
}
</code></pre>

上述结构和我们文中的第一个结果，因此可以进一步的对其中的元素做封装

比如我们对通常使用警告的颜色为红色, 但是我们红色提示的文字可能不同，此处我们封装一个危险的按钮的示例

<pre><code class="language-js line-numbers">const dangerButton =({text}) =&gt; ({
  type: Button,
  props: {
    color: 'red',
    children: text  
}
})
</code></pre>

比如书中给了一个很好的示例

<pre><code class="language-js line-numbers">const DeleteAccount = () = &gt;({
    type: 'div',
    props: {
        children: [{
            type: 'p',
            props: {
                children: 'Are you sure?',
            },
        },
        {
            type: DangerButton,
            props: {
                children: 'Confirm',
            },
        },
        {
            type: Button,
            props: {
                color: 'blue',
                children: 'Cancel',
            },
        }],
    }
});
</code></pre>

这是一个弹出的删除账户的组件，其中有文字以及确定和取消的按钮，删除账户的组件就完成了。

我们后面将继续介绍 JSX 的语法