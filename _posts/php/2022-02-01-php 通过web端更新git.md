---
layout: post
title: php 通过web方式更新git
categories: php
path: php
description: php通过web方式更新git
keywords: 通过web方式更新git
---

     
php需要打开ssh2 扩展 
   这是比较简单的方式  
    其他的方式 直接浏览器访问需要输入git用户名和密码，或者不是超管很麻烦   
    例如 
  
    shell_exec("/usr/bin/sh /www/wwwroot/bjldjjybproject2023/crmeb/public/bushu.sh 2>&1");  
    2>&1 必须写才能从页面看到报错信息  
基本   
   1.脚本 bushu.sh 

	#!/bin/bash
	cd  /www/wwwroot/gitdir
	git pull origin master

   2.php脚本bushu.php
     

	php web端执行shell 比较方便的方式
	
	$user="user";  //用户名
	  
	$pass="password";  //密码
	
	$connection=ssh2_connect('8.131.85.159',22);
	
	ssh2_auth_password($connection,$user,$pass);
	
	// 查看家目录的命令
	
	$cmd="/usr/bin/sh /www/wwwroot/bjldjjybproject2023/crmeb/public/bushu.sh";
	
	$ret=ssh2_exec($connection,$cmd);
	
	stream_set_blocking($ret, true);
	
	echo (stream_get_contents($ret));

 3.浏览器访问  
    http://www.web.com/bushu.php
 
  
