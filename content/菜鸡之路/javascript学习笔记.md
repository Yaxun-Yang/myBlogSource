---
title: "Javascript学习笔记"
date: 2020-04-06T19:24:10+08:00
draft: false
Tags:
- 坑
- 笔记
- javascript
- thymeleaf
---
在写下这篇文字的时候是没有过系统学习过 js 的，由于写的是一个java web项目，用到 js 在所难免，又无法用调试工具调试，唔，真的很浪费时间，不管怎么样，把发现记录在这里吧~

### 同一个页面中的 js 的引用次序
自己写了一个js由于使用了jquery语法，又要引用到jquery文件。这个jquery文件呢，在作为被包含的common类型页面top.html中其实是已经被引用过了的但是，自己写的js是放在\<head\>标签中，而对top页面的包含引用则是放在\<body\>中，所以就造成了先解析自定义js再解析jquery文件，从而自定义js表现为无效。
![javascript.PNG](../images/javascript.png)

### 作为thymeleaf内联函数的 js

正确的引用法：
```
 <script  th:inline="javascript"></script>
```
错误的引用法：
```
 <script type="text/javascript" th:inline="javascript"></script>
```

我猜大约是因为type属性和内联函数属性不匹配的原因，不如不写type属性，让它自动匹配好了