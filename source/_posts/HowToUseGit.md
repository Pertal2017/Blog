---
title: 如何使用Git
author: Pertal
top: false
cover: false
toc: true
mathjax: false
tags:
  - - Git
  - - SourceTree
  - - Github
summary: 这是一篇关于如何图形化(命令化暂时没补充)的教程，教你如何使用Git连接远程的Github仓库。
categories: uncategorized
abbrlink: ab8e450c
date: 2020-07-11 08:51:11
password:
---

<!-- 这里注释一上面可能常用的东西 -->

<!-- toc用于目录的展开默认无需更改 -->

<!-- tags与categories 一个是标签一个是文章分类 标签可以有多个 文章分类只能有一个 要注意 直接后面添加即可 -->

<!-- top 默认 false 这个是用来推荐文章的 -->

<!-- mathjax 默认是 false 如果以后要用到数学公式可以开启 -->

<!-- summary 写得是关于文章的摘要 -->

<!-- password用于对文章进行加密 这里需要利用SHA256算法加密 这里给个加密网址  https://tool.oschina.net/encrypt?type=2 -->



# 相关软件

## Git

Git是一个开源分布式版本控制系统，简单来说就如同**系统备份**可以备份你写的代码，并且可以回溯你之前的代码。

## SourceTree

SourceTree是一个**图形化**的Git客户端，简单来说就是能够让我们通过像操作Windows那样更加容易的完成自己的代码版本控制。

# 软件安装

## Git安装

Git的下载需要到其官网下载，这里给出其Windows版本的链接[Git For Windows](https://git-scm.com/download/win)，直接点击**Click here to download manually**即可下载适合自己版本的Git,至于安装无脑下一步即可。

## SourceTree安装

SourceTree的下载同样在其[官方网站](https://www.sourcetreeapp.com/)能够下载到，由于我自己已经安装了SourceTree所以这里给出[SourceTree安装（小白特别详细教程）](https://www.jianshu.com/p/dce21c4e88fc)。

# 创建属于自己的远程仓库

1. 在创建自己的远程仓库之前，我们需要拥有自己的GitHub账号，登录 [GitHub](https://github.com/)既可以创建，这里推荐**谷歌浏览器**因为其自带翻译功能，毕竟对于新手来说，英语也是一个门槛，在完成自己账号的创建登录之后选择上方的**加号**，选择**New repository**  

![UQEHaQ.png](https://s1.ax1x.com/2020/07/11/UQEHaQ.png)


2. 跳转页面后在**Repository name**中填入自己的仓库名，**Description**中填入对此仓库的描述，这里注意的是由于初期我们使用的是**SourceTree**因此勾选**Initialize this repository with a README**可以减少对仓库的初始化操作，交由Github完成，最后点击**Create repository**即可创建自己的GitHub远程仓库。

![UQEoqS.png](https://s1.ax1x.com/2020/07/11/UQEoqS.png)


3. 创建完成后，选择**Code**按钮，在**Clone With HTTPS**中会给出一个**URL**链接，复制这个链接即可。  
   Note:当然这里也可以选择**Use SSH**,通过SSH密钥的方式登入，这里不做赘述。

![UQE7Vg.png](https://s1.ax1x.com/2020/07/11/UQE7Vg.png)


4. 在本地打开我们的**SourceTree**按住**Ctrl+N**打开一个页面，选择上方的**Clone**填入**URL**以及**本地保存路径**点击**克隆**即可

![UQEIr8.png](https://s1.ax1x.com/2020/07/11/UQEIr8.png)


# 相关引用与推荐

1. [解决Github网页上图片显示失败的问题](https://blog.csdn.net/qq_38232598/article/details/91346392)
2. [SourceTree 入门教程](https://www.jianshu.com/p/11bba2b1e95d)
3. [如何在Github 的README.md文件中添加图片](https://blog.csdn.net/weixin_38419133/article/details/89412755?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-8.edu_weight&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-8.edu_weight)
4. <span style='color:red'> \*强烈推荐 </span>  [Git入门](https://www.imooc.com/learn/1052) *这个教程里面有Git命令方法与SourceTree使用方法，开始可以挑选SourceTree的方法*
5. <span style='color:red'> \*强烈推荐 </span> [天生不聪明](https://mp.weixin.qq.com/s?__biz=MzU4NTIxODYwMQ==&mid=2247483856&idx=1&sn=47a72cee1190aefc06c24fea78f78484&chksm=fd8cae96cafb2780f2634bbeece1608f321ea2698523869ff6d0c58497ad2dfbf5fa1233b0dd&token=88683563&lang=zh_CN#rd) *大牛的软文，可以看看参考一哈，也是本课程的作者*
6. <span style='color:red'> \*强烈推荐</span> [如果高效学习有什么秘诀的话，那就都在这里了](https://mp.weixin.qq.com/s?__biz=MzU4NTIxODYwMQ==&mid=2247483836&idx=1&sn=90854aa76507281403e4dd9cd434a12b&chksm=fd8caefacafb27ec78f999fde4f1217c04c6e2ff28cf51fe511d8fa29d484d9281ff91de8c9c&token=88683563&lang=zh_CN#rd) *同上*

# 后续补充 -- 这里是后续会补充的内容 ~~当然暂时是不会补充了~~

1. markdown的使用与安装
2. 如何使用GitBush进行操作