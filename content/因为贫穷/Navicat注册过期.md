---
title: "Navicat注册过期"
date: 2020-02-12T22:11:29+08:00
draft: false
Tags:
- 备忘录
- Navicat
- 数据库
---
### 长时间解决方案
下载软件`Navicat Keygen`

### 短时间解决方案
1. 关闭Navicat程序
2. 键盘按 win + R， 输入 regedit 调出 Windows 系统注册表。
3. 删除 HKEY_CURRENT_USER\SOFTWARE\PremiumSoft\Data:
4. 展开 HKEY-CURRENT_USER\SOFRWARE\Classes\CLSID，然后展开每一个子文件夹查看，如果里面只包含一个info文件夹，就删掉它

ps: 所有 CAFEEFAC 开头的文件夹不需要检查（没有 info）