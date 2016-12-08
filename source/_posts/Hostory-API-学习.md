layout: w
title: Hostory API 学习
date: 2016-12-08 09:07:30
tags:
- History API
---
## 引言

HTML5 History API 为开发者提供在不刷新浏览器页面的情况下修改 URL 的能力，在这之前，如果开发者修改 url 就会全页面刷新。History API 可以让我们灵活控制浏览器地址栏线上的内容，为我们的开发提供了更多的便利。在今天，单页面应用大行其道，除了 ajax 技术之外，History API 也功不可没，它为我们提供了更友好的地址栏接口，让地址栏地址更可读。

## History 对象

在浏览器的控制台中，查看history，我们可以看到 History 为我们提供的属性和方法。

### 属性

+ __`history.lenght`__
    历史回话个数，这个个数包括当前页，当打开一个浏览器的空白页面时，history.lenght = 1。
+ __`history.state`__
    当前回话的 state，state 可以是任意类型，它有 `history.pushState` 或 `history.replaceState` 的第一个参数定义。

### 方法

+ **`history.go([number])`**
    浏览器前进或回退指定步骤。参数小于 0 时，浏览器回退指定的步骤，参数大于 0 时，浏览器前进指定的步骤。如果参数值太大或者太小时，方法无效果。

+ **`history.back()`**
    浏览器回退到前一个页面。相当于点击浏览器的回退按钮。等价于 `history.go(-1)`。

+ **`history.forward()`**
    浏览器前进到后一个页面。相当于点击浏览器的前进按钮。等价于 `history.go(1)`。

+ **`history.pushState([data], [title], [url])`**
    向 history 栈中添加一个会话。参数 data 为会话中数据，可以开发者自定义。title 为页面标题，现在还没有浏览器支持。url 为会话的 url。pushState 后，浏览器地址栏会跟着变化，但页面不会刷新，history.length 的值 +1。

+ **`history.replaceState([data], [title], [url])`**
    修改 history 中当前的会话。参数 data 为会话中数据，可以开发者自定义。title 为页面标题，现在还没有浏览器支持。url 为会话的 url。replaceState 后，浏览器地址栏会跟着变化，但页面不会刷新，history.length 的值不变。

### 事件

+ **`popstate`**
    浏览器回退时触发 popstate 事件。`history.back()` 和 `history.go([number < 0])` 时也会触发 popstate 事件。