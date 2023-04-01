---
layout: post
title:  react-express-mongodb
categories: js
description: react-express-mongodb 搭建聊天
keywords: react
---

## 1、创建初始化react项目 使用cli
```shell
   npx create-react-app my-app
```
## 2、安装antd-mobile
```shell
   npm install antd-mobile --save
```
 + 同时引入样式,修改 src/App.css，在文件顶部引入 antd/dist/antd-mobile.css。
   ```js
   import 'antd/dist/antd-mobile.css'; // or 'antd/dist/antd.less'
   ``` 

## 3、脚手架创建成功后的项目结构是如下：
```shell
├── README.md
├── node_modules
├── package-lock.json
├── package.json
├── public
└── src

```
## 4、使用npm run eject 进行项目扩展 项目结构如下
``` shell
├── README.md
├── config
├── node_modules
├── package-lock.json
├── package.json
├── public
├── scripts
└── src
```
## 5、使用brew安装mongodb 
   + 由于mongodb不开源了，brew install mongodb 是无法安装的，使用社区版可以进行安装
  ```shell
      Error: No available formula with the name 'mongodb'
  ```
   + 设置
  ```shell
   brew tap mongodb/brew
  ```
   + 安装 安装MongoDB社区服务器的最新可用生产版本（包括所有命令行工具）。这将安装MongoDB 4.2.x
  ```shell
   brew install mongodb-community
  ```
   + 安装生产版本 安装MongoDB社区服务器和命令行工具的最新4.2.x生产版本：
   ```shell
   brew install mongodb-community@4.2
   ```
   + 安装MongoDB社区服务器和命令行工具的最新4.0.x生产版本：
   ```shell
    brew install mongodb-community@4.0
   ```
   + 安装MongoDB社区服务器和命令行工具的最新3.6.x生产版本：
   ```shell
    brew install mongodb-community@3.6
   ```
   + 仅安装最新的mongoshell以连接到远程MongoDB实例：
   ```shell
    brew install mongodb-community-shell
   ```
    如果报错如下：
   ```shelll
   An exception occurred within a child process
   An exception occurred within a child process:
   DownloadError: Failed to download resource "mongodb-community"
   Download failed: https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-4.2.0.tgz
   ```

   + 重新执行一下上面的命令
   ```shell
      brew install mongodb-community@4.2
   ```
   + 文件路径
   ```shell
   配置文件：/usr/local/etc/mongod.conf
   日志目录路径：/usr/local/var/log/mongodb
   数据目录路径：/usr/local/var/mongodb
   ```
   + 启动 && 停止 mongodb-community服务器 ,mongod作为服务运行

   若要launchd启动mongod立即重启也登录时，使用
   ```shell
      brew services start mongodb-community
   ```
   + 如果您mongod作为服务进行管理，它将使用上面列出的默认路径。要停止服务器实例，请使用：

   ```shell
   brew services stop mongodb-community
   ```
   + 手动启动 mongod
   如果您不想要或不需要后台MongoDB服务，您可以运行：
   ```shell
      mongod --config /usr/local/etc/mongod.conf
   ```

   注意：如果您不包含--config带有配置文件路径的选项，则MongoDB服务器没有默认配置文件或日志目录路径，并将使用数据目录路径/data/db。

   要mongod手动关闭，请使用admin数据库并运行db.shutdownServer()：
   ```shell
      mongo admin --eval "db.shutdownServer()"
   ```


