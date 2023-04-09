---
layout: post
title: php tinyProxy
categories: php
path: php
description: php tinyProxy
keywords: php tinyProxy
---


1.简单概述

TinyProxy介绍
TinyProxy是轻量级的开源 HTTP/HTTPS 代理守护程序(轻量级http代理服务器)，它从一开始就设计得既快又小，是一个理想的解决方案，适用于需要全功能HTTP代理的嵌入式部署等用例，但无法使用较大代理的系统资源。


	1. 安装 TinyProxy   
	  yum -y install tinyproxy
	
	2. 配置 TinyProxy  
	vim /etc/tinyproxy/tinyproxy.conf    
	修改 Port 端口，默认为 8888  
	Port 8888  
	注释掉 Allow，表示允许所有人访问代理  
	#Allow 127.0.0.1
	
	3. 启动 TinyProxy  
	systemctl start tinyproxy.service  
	更多命令如下： 
	systemctl restart tinyproxy.service 
	systemctl stop tinyproxy.service 
	systemctl status tinyproxy.service 
	systemctl enable tinyproxy.service 


2 php curl 调用方法
  
	function curl($url, $data)
	{
	    $ch = curl_init();
	    curl_setopt($ch, CURLOPT_URL, $url);
	    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
	
	   /*代理用的**/
	    curl_setopt($ch, CURLOPT_PROXY, "111.229.27.225");
	    curl_setopt($ch, CURLOPT_PROXYPORT, "8100");
	    /*代理用的**/
	
	    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
	    curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);
	    // POST数据
	    curl_setopt($ch, CURLOPT_POST, 1);
	    // 把post的变量加上
	    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
	    $output = curl_exec($ch);
	    curl_close($ch);
	    return $output;
	}