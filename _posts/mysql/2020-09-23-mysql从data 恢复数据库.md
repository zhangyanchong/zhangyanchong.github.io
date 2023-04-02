---
layout: post
title: mysql从data 恢复数据库
categories: mysql
path: mysql
description: mysql从data 恢复数据库
keywords: mysql
---

	服务器系统突然崩溃，数据库又没有备份，只有原数据库文件夹存在。下面简单说一下通过这些数据库文件恢复数据。

	1、安装与原数据库相同版本的 mysql，如：原来安装的是mysql-5.5.59-winx64，现在再次安装这个版本

	2、mysql 可以正常启动、访问后，停止 mysql 服务。如：命令行停止数据库 管理器停止 mysqld.exe 的进程树。

	3、将原 data 下需要恢复的数据库文件夹（与数据库名同名）复制到新 data 下。

	4、将原 data 下的这五个文件 auto.cnf,ib_buffer_pool,ib_logfile0,ib_logfile1,ibdata1 复制并覆盖新data下的同名文件。

	5. 直接复制文件是无法使用的，会提示表不存在，在复制的时候，应将数据目录下的ibdata1文件一并复制过去，并且删除ib_logfile0，ib_logfile1等文件

	6.启动服务器查看 mysql 表 的情况