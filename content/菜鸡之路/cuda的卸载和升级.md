---
title: "Cuda的卸载和升级"
date: 2020-09-13T20:24:08+08:00
draft: false
---
## 背景
   学长给布置任务，叫我把实验室里某台ubuntu16.04的cuda从9.0升级成10.01， 对应的cudnn和drivers都给整配套， 于是开始了这个不太难却颇为纠结的工作，全程大约花费一个上午加一个晚上
   官网是文档步骤什么的其实挺清晰的，坑也不少，在此记录
## 常规操作
1. 检查各种前置准备，官网文档这一块说的很清楚，就是看内核版本、看gcc版本什么之类的，基本没问题
2. 内核需要注意的一点是，可能计算机在你不知道的时候有多个内核， 进入`/boot`文件夹可以看到，然后移除多余版本的内核<-[参考](https://zhuanlan.zhihu.com/p/50033643)
3. 移除原有的驱动和cuda
   [cuda和cudnn的卸载](https://blog.csdn.net/wanzhen4330/article/details/81704474)
   [drivers的卸载](https://blog.csdn.net/ezhchai/article/details/80536949)
4. 有尝试在安装cuda的同时安装驱动然后惨烈报错，看大量blog似乎都是先安装驱动然后安装cuda，遂尝试
5. 驱动安装[参考](https://zhuanlan.zhihu.com/p/143429249)
6. cuda安装，我这里采用的是run安装包，输入[官网](https://developer.nvidia.com/cuda-toolkit-archive)显示的安装命令，由于提前装好了drivers， 所以在选择组件的时候去掉driver
7. [配置环境变量、并通过sample检查cuda是否正常安装](https://zhuanlan.zhihu.com/p/143429249)(看到Result = PASS的时候我一定哭了，呜呜呜呜)
8. 然后需要安装cudnn，注意[版本之间的匹配](https://blog.csdn.net/qq_27825451/article/details/89082978)
（9. 到cudnn官网下载， 下载需要注册账号（注册账号这个事情就很麻烦……而且似乎对outlook邮箱不太友好？），注意三个文件都需要下载，并安装
10. 测试cudnn的安装情况， 得到“Test Passed”,快乐！）
9.[下载cudnn的library包， 并使得cuda包含它] (https://www.jianshu.com/p/e22866b72f43)

