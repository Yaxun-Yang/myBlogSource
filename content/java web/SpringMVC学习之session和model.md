---
title: "SpringMVC学习之session和model"
date: 2020-04-02T21:25:23+08:00
draft: false
Tags:
- SpringMVC
- 课程学习
- 笔记
- 理解
---

## 情景描述
在写鸟店的项目中，在多个页面需要用到account的信息，在myPetStore1.0里，使用session实现account长时间缓存。在SpringMVC中则不推荐使用account ， 铁哥有告诉我们用到“@SessionAttributes”标签和其它几个类似标签，但是并未具体说明，在做了一些实验，看了一些资料之后，写下我的理解。
## 理解
@SessionAttributes（value={"att1","att2","att3"},types={Class1.class,Class2.class}）：用于类，被value注释了名字的属性和被types注解了类型的属性将会在被加入model之后被自动加入session。取两种集合的并集。
需要特别注意的是，加入session的操作，大约是在整个被调用方法执行之后，具体表现为：
```
model.addAttribute("account",account);
System.out.println(httpServletRequest.getSession().getAttribute("account"));
----
null
```
这样随后从session中取值，取到的实际上是空值

通过 SessionStatus的setComplete()方法可以清空SessionAttribute中的数据

@ModelAttribute("att")：用在方法，意义是使得方法中的被注释的属性自动加入model

@SessionAttribute（value="att"）： 用在属性，访问预先存在的全局会话属性，可使得被注释的属性被注入存在SessionAttribute中的值