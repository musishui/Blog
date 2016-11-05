title: css 实现固定宽高比
date: 2016-11-05 18:44:46
tags:
    - css
    - margin
    - padding
    - 伪元素
---

## 问题

以前遇到一个需求，页面显示一个弹窗，弹窗宽度是随页面宽度变化而变化的，要求弹窗的高度和宽度以一个固定的宽高比显示，当时使用js来监听window的resize事件实现的，现在回头看看，完全可以用css实现。

## 实现

先看代码

``` css
.box{
        width: 50%;
        position: relative;
}
.fill{
        height: 0;
        padding-bottom: 60%;
}
.content{
        width: 100%;
        height: 100%;
        position: absolute;
        background: #ccc;
        left: 0;
        top: 0;
}
```

``` html
<div class="box">
    <div class="fill"></div>
    <div class="content"></div>
</div>
```
<style>
.box{
        width: 50%;
        position: relative;
        background: #ccc;
}
.box .fill{
        height: 0;
        padding-bottom: 60%;
}
.box .content{
        width: 100%;
        height: 100%;
        position: absolute;
        background: #ccc;
        left: 0;
        top: 0;
        font-size:20px;
}
</style>

<div class="box"><div class="fill"></div><div class="content">Example</div></div>
主要实现思路是先定义一个容器 `div.box`，设置它的 `positin` 为 `relative` , 用一个 `div.fill` 填充它，设置这个div的 `height` 为 `0` , `padding-bottom` 为 `60%` , 这个 div 负责把外层的 div 的高度撑起来，并且是按照宽高比 `5:3(100%:60%)` 的固定比例，再放一个内容 `div.content` , 设置宽高同为 `100%`, `positin` 为 `absolute`，现在这个基本上就满足需求了。当然，这个需求还有别的解决方案，但思路基本上是一致的。



## 其他实现

+ 利用 `margin` 实现

``` css
.box{
        width: 50%;
        position: relative;
        overflow: hidden;
}
.fill{
        height: 0;
        margin-bottom: 60%;
}
.content{
        width: 100%;
        height: 100%;
        position: absolute;
        background: #ccc;
        left: 0;
        top: 0;
}
```

``` html
<div class="box">
    <div class="fill"></div>
    <div class="content"></div>
</div>
```

+ 利用 `:before` 或 `:after` 伪元素实现

上面两种实现方式有一个共同的缺点，增加了一个 `div.fill` 元素，这个元素可以用伪元素替换。
``` css
.box{
        width: 50%;
        position: relative;
        overflow: hidden;
}
.box:before{
        height: 0;
        display: block;
        margin-bottom: 60%;
}
.content{
        width: 100%;
        height: 100%;
        position: absolute;
        background: #ccc;
        left: 0;
        top: 0;
}
```

``` html
<div class="box">
    <div class="content"></div>
</div>
```