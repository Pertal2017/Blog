---
title: Github+Hexo搭建博客教程
author: Pertal
top: true
cover: false
toc: true
mathjax: false
tags:
  - [Github]
  - [Hexo]
categories: 教程
abbrlink: 19f3ab51
date: 2020-07-10 11:56:25
password:
summary: Github+Hexo搭建教程，是自己搭建时的一些总结，希望对大家有用。
---

# 前言

因为毕业了，所以为了以后能够有一个记录的博客，所以花费了一段时间，搭建了一个利用GitHub+Hexo实现的个人博客~~(最大的原因是因为可以白嫖)~~ ，但是之前使用的博客没有用过Markdown进行相关的内容写作，因此教程可能有些地方并不美观，还请各位小伙伴能够见谅，有问题也可以在下方留言，有时间我会回答的。

首先我们要了解一下我们搭建博客需要使用的框架Hexo，这个框架是一个高效的静态站点生成框架，基于Node.js。通过这个框架我们可以利用MarkDown语法来撰写自己的博客内容，并且写文章，除了没有可视化管理界面以外一切都很方便(这个问题可以用插件解决)，废话少说下面介绍。

# 准备与安装

在这搭建自己的博客之前我们需要完成三个主要的步骤，首先要拥有你自己的**Github账号**其次要在你的系统中安装好**Git**以及**Node.js**。

## Github的注册

[Github](https://www.github.com) 的注册网上有很多的教程，由于我自己已经有了一个Github账号，因此这里给出网上比较新的注册教程，虽然GIthub网站是英文的网站，但是一般的浏览器都自带翻译功能，相信这个难不倒各位————[Gihub注册教程](https://blog.csdn.net/JCtry/article/details/107191143)

## Git的安装

因为我们需要把自己本地仓库的内容上传到Github上面去，所以我们可能需要用到版本控制工具[Git](https://git-scm.com/downloads)，由于这个工具并不是GUI工具所以可能需要学习一些命令，本文需要用到的命令下面都会标出，这里同样给出一个[Git的安装教程](https://blog.csdn.net/aiwst/article/details/106924863)照着安装即可。

**Note：**

​	这里提示一下，添加路径的时候要选择 `Use Git from the Windows Command Prompt`,这样做的好处可以让我们在Windows的控制台打开Git。安装完成之后Windows系统下按住`Win+R`输入`cmd`打开控制台输入`git --version`验证是否安装成功，效果如下图：

<img src="https://s1.ax1x.com/2020/07/10/UuXJvq.png" alt="UuXJvq.png" style="zoom:85%;" />

## Node.js的安装

[Node.js](https://nodejs.org/en/)安装就比较简单了直接点击[下载](https://nodejs.org/dist/v12.18.2/node-v12.18.2-x64.msi)其实就可以了，我这里给出的是长期支持的x64版本如果需要其他版本可以上官网查看，安装只需要一路Next即可。

安装完成之后Windows系统下按住`Win+R`输入`cmd`打开控制台,输入 `node -v` 和 `npm - v` ,如果出现版本号，就安装成功了，如下图：

![UuXfaD.png](https://s1.ax1x.com/2020/07/10/UuXfaD.png)



当上面的步骤完成之后，我们就可以开始利用我们的Github搭建我们自己的免费博客了！

# GithubPage设置

## GithubPage仓库创建

GithubPage是Github提供的一个搭建博客的功能，利用这个我们可以免费搭建属于自己的个人博客，打开https://github.com ,新建一个项目，如图所示：

![UujmW9.png](https://s1.ax1x.com/2020/07/10/UujmW9.png)

之后输入自己的项目名字，项目名为 `创建的用户名.github.io` 注意的是这里的 `.github.io` 不能少，同样的你的用户名必须和你的**Github用户名**完全一致，不能改动，例如我这里的账号叫 `PertalDemoTest` ,那么我创建的 `repository` 名称就叫 `PertalDemoTest.github.io` , 下面的 `Description` 用来填写对这个仓库的描述，其他默认即可，当然这里可以**勾选**`Initialize this repository with a ReADME`，这样可以直接初始化，这里我就不勾选了。

![UKSBcj.png](https://s1.ax1x.com/2020/07/10/UKSBcj.png)

创建完成之后，出现的界面如下所示:

<img src="https://s1.ax1x.com/2020/07/10/UKSqUK.png" alt="UKSqUK.png" style="zoom:50%;" />

到这里基本的仓库创建就完成了。

## 如何利用Git进行初始化

完成了仓库的创建之后，我们需要对我们自己新建的这个仓库进行一个初始化，这里首先在本地新建一个文件夹用来保存后续上传到仓库的配置，对文件夹**鼠标右键**后选择**Git Bash Here**弹出Git的界面后，我们首先进行c初始化输入 `git init` 之后一下设置用户名和邮箱的设置，这里分别输入 `git config user.name "你的Github用户名"` 和 `git config user.email "你创建的Github账户邮箱"` 当然 如果你只有一个账户的话可以直接设置 `git config --global user.name "你的Github用户名"`和 ``git config --global user.email "你创建的Github账户邮箱"`` 设置完成。

![UKPWZR.png](https://s1.ax1x.com/2020/07/10/UKPWZR.png)

这里我们使用**SSH**的登入方式，因为这种登录方式比较简单，直接输入 `ssh-keygen -t rsa -C "你的电子邮箱"`即可，然后一路回车，如果碰到有**(y/n)**打一个**y**继续回车，这样我们就生成了自己的SSH密钥。

![UKimWT.png](https://s1.ax1x.com/2020/07/10/UKimWT.png)

然后打开你的Github找到**Settings**，找到**SSH and GPG keys**点击**New SSH key**之后到你的 `C:/用户/你的用户名/.ssh`下找到`id_rsa.pub`文件利用**记事本**打开复制里面的内容，放入刚刚的页面中，这里的**Title**可以随意，如下图所示：

![UKkSKg.png](https://s1.ax1x.com/2020/07/10/UKkSKg.png)

![UKATAA.png](https://s1.ax1x.com/2020/07/10/UKATAA.png)

同时这里设置一下，可能需要输入一下自己的密码，验证一下，之后我们在控制台中输入 `ssh -T git@github.com` 出现下图提示就成功了。

![UKZxBD.png](https://s1.ax1x.com/2020/07/10/UKZxBD.png)

需要注意的是后面提示没有提供**shell access**这里我们需要在个人账户的设置中找到**Email**设置下将**Keep my email address private**的勾选取消，然后在**Profile**设置中找到**Public email**选择自己的邮箱拉到下面点击**Update profile**解决后面**无法push**的问题。

接下来我们可以参照**Github的提示**测试一下连接我们的远程仓库

![UKmjTe.png](https://s1.ax1x.com/2020/07/10/UKmjTe.png)

[![UKnmfs.png](https://s1.ax1x.com/2020/07/10/UKnmfs.png)](https://imgchr.com/i/UKnmfs)

之后刷新一下我们的仓库，可以看到一个`README.md`文件，到这里我们已经完成了本地与远程仓库的连接。

## 安装Hexo

接下来，刷新一下我们的仓库页面，找到**Settings**下拉找到**GitHub Pages**点击**Choose a theme**选择一个喜欢的主题，选择**Select theme**然后在网址框中输入`你的用户名.github.io`可以发现已经有一个页面的雏形了。

![UKuZDK.png](https://s1.ax1x.com/2020/07/10/UKuZDK.png)

接下来我们就开始安装Hexo,在Git控制台中输入 `npm i hexo-cli -g` ，可能会有**WARN**这里可以直接无视，接下来输入 `hexo init` 进行初始化，然后输入 `npm install` 安装必备组件，这里可能有报错，我们可以将隐藏的 `.git`先移到别处删除我们刚刚创建的`REAMD.md`文件,等待安装结束后在移回来，接下来我们输入 `hexo g` 和 `hexo s` 然后浏览器输入http://localhost:4000/ , 就可以看到我们的博客啦，效果如下：

![UK1iXn.png](https://s1.ax1x.com/2020/07/10/UK1iXn.png)



到这里整个博客就算搭建完成了，接下来我们就可以写我们自己的文章了。

# 写文章，发布文章

首先安装一个扩展 `npm i hexo-deployer-git` 然后输入 `hexo new "文章名"`就可以创建一篇文章啦，之后打开 `根目录/source/_posts`里面就可以发现创建好的文章，这里编写文章可能需要学习一下MarkDown，并且下载一个支持`.md`文件的程序，这里我用的是[Typora](https://www.typora.io/),当然市面还有其他各类的软件，这里就看个人喜好进行选择了，编写完成后 打开**根目录**下的 `_config.yml` 文件修改**deploy**后保存。

```
deploy:
  type: git
  repository: https://github.com/你的github用户名/你的github用户.github.io
  branch: master
```

 `hexo g` 生成文件然后`hexo d`就可以将自己的文章发布到网站上了，输入 `用户名.github.io` 就可以访问自己刚刚生成的文章了，到这里基本的博客就搭建完成了。

# 个性化设置

这里埋一个坑，内容很多，慢慢填坑...