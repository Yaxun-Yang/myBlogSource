---
title: "基于hugo的个人博客"
date: 2020-01-29T08:30:14+08:00
draft: false
Tags:
- hugo
- blog
---


  之前学算法的时候就一直想建一个自己的blog, 对一个学了忘的家伙来说，把学了的东西记下来的确能省不少事，一直懒惰，知道后来听学姐说找出国可能会用到，也就莫名奇妙有了个执念，那么就折腾折腾吧。
  先看的大量 blog, 感觉推荐 hexo 框架的比较多，后来发现有人说hexo部署太慢， 不如换成 hugo, 唔，那就换成hugo吧 。

---
# 参考文章

> - [hugo中文帮助文档](https://hugo.aiaide.com/)
> - [如何搭建你自己的博客（一系列文章）](https://dp2px.com/2019/09/11/build-web/)本墙头草从hexo转向hugo的根本原因
> - [页面改造模板说明](https://blog.csdn.net/weixin_44397907/article/details/99621517)
> - [一篇官网地址和各类配置格式汇总的博客](https://youendless.com/post/hugo_blog/)

-----
# 常用命令
- `hugo server` 本地预览 https://localhost:1313
- `hugo` 部署服务器（修改pubulic目录）
- `hugo new site SITEADRESS/SITENAME` 新建一个基站
- `hugo new POSTADRESS/POSTNAME` 新建一篇文章

---
# 坑点 
- 当希望使用tag等的时候,需要在'config.toml'中添加，双引号内内容固定
```
[taxonomies]
	tag = "tags"
	category = "categories"
	series = "series"
```
- 不要在描述 tags 的时候使用中文的“、”；
- 在每个tag具体内容与`-`之间必须有空格
- 使用 github 作为基站的时候注意将库公开，才能部署在github page 上。
- 放在static文件夹里的资源会被放在根目录，但是以绝对路径去获取却获取不到，需要从文章跳出一层当前文件夹，这样的相对路径获取


----
# 待解决
有心情再解决吧，本强迫症觉得那一天并不远
- 网页刷新速度慢
- 主题页面和文章页面想使用不一样的模板
