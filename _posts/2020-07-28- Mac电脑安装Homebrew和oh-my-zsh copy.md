---
layout: post
title: Mac电脑安装Homebrew和oh-my-zsh
categories: mac
description: Mac,Homebrew oh-my-zsh
keywords: Mac,Homebrew oh-my-zsh
---

### 1、下载 homebrew 执行如下命令

```shell
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- 可能有报错情况，貌似 github 的一些域名的 DNS 解析被污染，导致 DNS 解析过程无法通过域名取得正确的 IP 地址。

### 解决方案

打开 https://www.ipaddress.com/ 输入访问不了的域名
例如：githubusercontent.com

查询之后可以获得正确的 IP 地址

在本机的 host 文件中添加，建议使用 switchhosts 方便 host 管理

199.232.68.133 raw.githubusercontent.com
199.232.68.133 user-images.githubusercontent.com
199.232.68.133 avatars2.githubusercontent.com
199.232.68.133 avatars1.githubusercontent.com

添加以上几条 host 配置，页面的图片展示就正常了，homebrew 也能装了，nvm 也行动灵活了。
