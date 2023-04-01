---
layout: post
title: Mac 中安装、使用 git 和 Sourcetree
categories: git
description: Mac 中安装、使用 git 和 Sourcetree
keywords: Mac, git, Sourcetree
---
## git安装
1、[git官网](https://git-scm.com/)下载dmg文件直接安装

2、用brew install git安装

## key问题
查看mac上是否已经存在key
``` sh
$ cd /Users/liufangting/.ssh
```
如果没有，即生成新的key
``` sh
$ ssh-keygen -t rsa
```
把公钥上传到gitlab的ssh-keys,这个地方支持上传多个key,因此不用担心覆盖掉了windows及其它设备的key

## 在mac上初始化git(设置全局属性)
每个机器都必须自报家门：你的名字和Email地址
``` sh
$ git config --global user.name liu.yw-mac
$ git config --global user.email liu.yw@wonhigh.cn
```
注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

## 设置版本库（本地仓库）
版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

创建一个版本库非常简单，首先，选择一个合适的地方，创建一个空目录：
``` sh
 $ mkdir my_git
 $ pwd
 $ /Users/liufangting/my_git
 ```

 第二步，通过git init命令把这个目录变成Git可以管理的仓库：
 ``` sh
 $ git init
Initialized empty Git repository in /Users/liufangting/my_git/.git/
```
一个空的仓库（empty Git repository）就建好了，没事不要去修改隐藏目录.git的文件，这个目录是Git用来跟踪管理版本库的，改乱了，就把Git仓库给破坏了。

## Git基本操作
1、把文本添加到版本库
创建一个test.txt文件，内容如下：
``` sh
Git is a version control system.
Git is free software.
```
文件一定要存放在/Users/liufangting/my_git目录或者其子目录下，要不然git会找不到

2、用命令git add告诉Git,把文件添加到仓库
``` sh
$ git add test.txt
或者
$ git add --all
```
3、用命令git commit告诉Git,把文件提交到仓库
``` sh
$ git commit -m "wrote a test file"
```
4、克隆代码库
``` python
$ git clone ssh://git@gitlab.belle.cn:10022/dev/bf-config-new.git
Cloning into 'bf-config-new'...
The authenticity of host '[gitlab.belle.cn]:10022 ([172.20.32.132]:10022)' can't be established.
ECDSA key fingerprint is SHA256:/Xac/5alCkOVwE0zet2N+vJ9oWuej1giAo+lv5PMxzc.
Are you sure you want to continue connecting (yes/no)? yes
```
这里提示yes/no ,要输入yes,不然clone失败

5、拉取代码
``` sh
$ git pull
```
6、提交所有改动
``` sh
$ git commit -am "注释内容"
```
7、推送到服务器
``` sh
$ git push
```
8、随时掌握工作区状态
``` sh
$ git status
```
9、查看文件修改内容，常和git status一起用
``` sh
$ git diff
```


## 注意的问题和Git的局限性
1、Git只能版本控制纯文本文件，对于图片，视频和word文档这些二进制格式的文件，无法追踪内容的改动，只能看到文件大小的变化

2、文本编码建议使用标准的UTF-8编码，即解决冲突又为所有平台所支持

## 参考资料
[廖雪峰的博客](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

# Sourcetree安装配置
[官网](https://www.sourcetreeapp.com/)下载Mac版的安装包，直接拖到“应用程序”就可以

Sourcetree是免费的开源软件，但是要注册后免费使用，特别是新版一定要输入注册的用户名和密码（不可以跳过）才能正常使用。注册的时候要输入一个邮箱号来接收确认邮件，我是用QQ邮箱才注册成功的（163的邮箱不行），即使用QQ邮箱确认邮件也有延迟，隔了一晚上才收到，所以暂时没有收到确认邮件不要着急上火。

软件开启来后，一般是要“添加已经存在的仓库”，这时候在Mac上会出现选择不到本地仓库文件夹的情况，此时需要在打开“finder”在finder的“偏好设置”中“边栏”选项，把个人家目录，相关的图片，音乐文件夹什么的勾选显示在“个人收藏”中，这样就方便在界面上选择了。

有很多工程项目的时候，可以在sourcetree里建立分组文件夹，加以区分，会清晰很多，形如这样的就很好：

![aa1](/images/posts/mac/markdown-img-paste-20180302163956748.png)
