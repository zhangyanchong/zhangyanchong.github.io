---
layout: post
title: 在 Mac 上安装软件
categories: mac
description: Mac 安装软件的方法
keywords: Mac, Mac OSX, Homebrew
---


## 在App store安装软件
这个最简单，找到软件，点获取就可以，前提是注册个苹果账户，很多软件是付费的。
## 安装.dmg程序
Mac系统的安装文件后缀名是.dmg,  双击打开后，会出现一个安装对话框， 把图标拖拽到Application中就可以了,如果是版本升级，也可以如此操作，拖进去后选择一下替换就行。

![](/images/posts/mac/markdown-img-paste-20180302150418632.png)

## 使用brew在Mac上安装软件
brew全名叫Homebrew，是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件， 只需要一个命令， 非常方便。
brew类似centos的yum或者ubuntu的apt-get
## 安装brew
在官方网站： http://brew.sh/   有对brew用法详细描述

安装方法：在Mac中打开终端输入命令：
``` python
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install )"
```
![a2](/images/posts/mac/markdown-img-paste-2018030214452936.png)

下载安装完成大概20分钟（100M电信光纤实测）

## 使用brew安装软件
安装git,一键搞定，是不是很爽
``` python
brew install git
```
再安装个wget
``` python
brew install wget
```
## 使用brew卸载软件
``` python
brew uninstall wget
```
![a3](/images/posts/mac/markdown-img-paste-20180302144649433.png)

## 使用brew查询软件
不知道软件的准确名字，先搜索查询一下
比如要安装
``` python
brew search /wge*/
```
/wge*/是正则表达式，星号要包含在/内

![a4](/images/posts/mac/markdown-img-paste-20180302144751884.png)

## 其它brew命令
brew list     列出己安装软件

brew update   更新brew

brew home     用语浏览器打开brew官网

brew info     显示软件信息

brew deps     显示包依赖
