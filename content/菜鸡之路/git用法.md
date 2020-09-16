---
title: "Git用法"
date: 2020-01-29T08:27:49+08:00
draft: false
Tags:
- git 
- 备忘录
---

  作为新手村玩家，不学 git 实在说不过去，奈何本人记性实在不好，顺手在这里把一些常用用法 mark 一下。小伙伴有推荐 git 的傻瓜式可视化工具Github Desktop，但是个人觉得不如命令行灵活好用，这里就单纯 mark 教程吧。

---
# 教程
- [廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600)
- [Github Desktop](https://www.jianshu.com/p/06a960d991aa)
- [一条龙初学者教程](https://www.cnblogs.com/tugenhua0707/p/4050072.html#!comments)

---
# still puzzle
- [git 子模块](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)
---
 # 常用命令
 - 连接远程库
 ```
    git remote add origin git@git.com:Yaxun-Yang/adversarial_examples_renderer.git
 ```
- 将(master)内容推到远程数据库
```  
  git push -u origin (master)
```
- 修改现有远程库
```
git remote set-url origin git@git.com:Yaxun-Yang/adversarial_examples_renderer.git
```
- 查看是否连接远程库
```
git remote -v
```
- 添加文件至缓存区
``` 
git add .
```
- 添加版本库(添加说明)
``` 
 git commit (-m "*****")
```
- 清空工作区（但保存现场可恢复）
```
git stash
```
- 查看缓存区修改内容（恢复现场）
```
 git status
```
- 清空缓存区内容
``` 
git reset .
```
- 还原修改
```
git checkout .
```
- 删除新建文件和文件夹
```
git clean -d
```
- 查看具体文件的具体修改事项
```
git diff readme.txt
```
- 由近至远显示提交日志(简洁版显示)
 ```
 git log  (-pretty = online)
 ```
- 回退上上个版本
```
 git reset -hard HEAD^^
```
- 回退上一百个版本
```git
git reset -hard HEAD~100
```
- 查看本地分支
```
git branch
```

- 查看远程分支
```
git branch -r
```
- 拉取远程分支并进入该分支
```
git checkout -b 本地分支名 origin/远程分支名
```
- 拉取远程分支但不进入该分支
```
git fetch origin 远程分支名：本地分支名
```
- 切换分支
```
git checkout 分支名
```


