title: "Ractive 基础教程（一）模板"
date: 2015-11-27 14:14:15
tags: 
- ractive
- template
---
## 概述
在Ractive中，模板可以简单的理解成一段加了逻辑的Html代码片段，它遵循[Mustache](http://mustache.github.io/)语法规范，是[Mustache](http://mustache.github.io/)的超集。模板应该是格式良好的代码片段，Ractive的模板解析器不能像浏览器一样兼容格式不好（比如说标签没有闭合）的Html代码。

理解Ractive模板，可以从两点出发:

+ 首先它是Html片段，它的主体结构是Html标签，这和我们平时在页面上写的Html标签并没有什么不一样。

+ 其次，模板是加了逻辑的（可编程）代码片段，在一般的Html页面中使用Html标签仅仅是进行展示，页面上的两个div是没有直接关系的，如果想要把这两个div联系起来，必须借助JavaScript编程。而模板中的Html是可以添加一些逻辑判断的，比如循环、条件控制等，我们可以通过对模板进行编程来使模板中的标签产生内在的联系。

## 语法
### 变量（Variables）
变量可以用`{{变量名}}`、`{{{变量名}}}`来定义，当实例化模板时，模板引擎会在数据对象中查找对应的变量值替换模板中的变量。
``` javascript
// 模板
1-{{name}}
2-{{age}}
3-{{title}}
4-{{{title}}}

// 对象
{
	name:'musishui',
	title:'<h1>GitHub</h1>'
}

// 输出
1-musishui
2-
3-&lt;h1&gt;GitHub&lt;/h1&gt;
4-<h1>GitHub</h1>
```
### 片段（Sections）
片段可以用`{{#变量名|表达式}}...{{/变量名|表达式}}`来定义，
