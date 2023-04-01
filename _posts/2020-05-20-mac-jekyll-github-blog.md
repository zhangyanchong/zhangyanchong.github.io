---
layout: post
title: Mac下使用Jekyll和github搭建个人博客
categories: mac
description: Mac下使用Jekyll和github搭建个人博客方法
keywords: Mac, Jekyll, Github
---

## 1、安装ruby
使用brew安装
``` python
$ brew install ruby
```
查看ruby版本
``` python
$ ruby -v
ruby 2.5.0p0 (2017-12-25 revision 61468) [x86_64-darwin17]
```
## 2、安装gem
Mac机器已经自带gem,没有gem的[参考网站](https://rubygems.org/pages/download)安装
``` python
$ gem -v
2.7.4
```
给gem更换国内的源，原始源由于“墙”的原因，很蛋疼
``` python
# 查看原始源列表
$ gem sources -l
https://rubygems.org/

#将源移除
$ gem sources --remove https://rubygems.org/

#添加国内源
$ gem sources --add http://gems.ruby-china.org/

#缓存源
$ gem sources -u

#再次查看源列表，确认源已更新
$ gem sources -l
http://gems.ruby-china.org/
````
注意：这里使用http://gems.ruby-china.org ，而不是 https://gems.ruby-china.org ，是因为可能有SSL证书问题

## 3、安装jekyll
``` python
$ sudo gem install jekyll
```

## 4、安装博客
安装以下组件
``` python
1 $ sudo gem install bundler
2 $ sudo gem install jekyll-paginate
3 $ sudo gem install jekyll-gist
```
创建博客(如果没有找到jekyll命令，重启下终端)
``` python
$ sudo jekyll new echomusicblog
```
安装过程会显示一堆安装内容，关注最后一行
``` python
New jekyll site installed in /Users/liufangting/echomusicblog.
```

## 5、本地启动博客
进入到安装目录执行命令
```python
$ cd /Users/liufangting/echomusicblog
$ sudo jekyll serve
```
输出
``` python
Password:
Configuration file: /Users/liufangting/echomusicblog/_config.yml
            Source: /Users/liufangting/echomusicblog
       Destination: /Users/liufangting/echomusicblog/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.415 seconds.
 Auto-regeneration: enabled for '/Users/liufangting/echomusicblog'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```
将http://127.0.0.1:4000/复制到浏览器，能打开就表示正常了。
![WX20200525-173904.png](https://i.loli.net/2020/05/25/9wAstdqeESUZQRP.png)

## 6、部署到github
&emsp;&emsp;按照自己的github账号创建一个仓库,固定格式username.github.io，这个代码仓库就是博客源码存放地，博客公网链接就是：https://echo-music.github.io
``` python
https://github.com/echo-music/echo-music.github.io.git
```
将本地内容和github上的仓库关联
``` python
1 $ cd /Users/liufangting/echomusicblog
2 $ sudo git init
3 $ sudo git add .
4 $ sudo git commit -m "first commit"
5 $ sudo git remote add origin https://github.com/echo-music/echo-music.github.io.git
6 $ sudo git push -u origin master
```
&emsp;&emsp;这里注意替换为你自己的地址，在执行git push的时候，需要输入github的账号和密码。
完成后在浏览器上输入: echo-music.github.io，就可以看见博客了。

## 7、使用主题
&emsp;&emsp;使用jekyll new出来的博客实在是太原始，太简陋，完全没有“高大上”的感觉，我们需要“高颜值”的主题（对于 jekyll ，主题就是一套完整的博客框架源码），[jekyllthemes](http://jekyllthemes.org/)提供了很多的主题，比如我选择的主题就是基于[yummy-theme](http://jekyllthemes.org/themes/yummy-theme/)扩展的。

&emsp;&emsp;把自己的github 空仓库git clone 到本地，拿到的框架源码拷贝到空仓库目录下
``` python
$ git clone https://github.com/echo-music/echo-music.github.io.git
```
&emsp;&emsp;刚拿到的主题，内容还是别人的，我们需要了解一下博客的[基本目录结构](https://www.jekyll.com.cn/)，然后加以修改成自己的博客框架。

![1591254493711.jpg](https://i.loli.net/2020/06/04/Wbhv19f2sYZ7XeB.jpg)

1. 修改域名

   如果你需要绑定自己的域名，那么修改 CNAME 文件的内容；如果不需要绑定自己的域名，那么删掉 CNAME 文件。

2. 修改配置

   网站的配置基本都集中在 \_config.yml 文件中，将其中与个人信息相关的部分替换成你自己的，比如网站的 url、title、subtitle 和第三方评论模块的配置等。

3. 删除文章与图片

   如下文件夹中除了 template.md 文件外，都可以全部删除，然后添加自己的内容。

   * \_posts 文件夹中是已发布的博客文章
   * \_drafts 文件夹中是尚未发布的草稿文章
   * \_wiki 文件夹中是已发布的 wiki 页面
   * images 文件夹中是文章和页面里使用的图片

4. 修改「关于」页面

   pages/about.md 文件内容对应网站的「关于」页面，里面的内容多为个人相关，将它们替换成自己的信息，包括 \_data 目录下的 skills.yml 和 social.yml 文件里的数据。

5. 修改 favicon.ico 图标，选一个自己喜欢的图标替换

经过以上整理，一个全新的博客框架基本成型，后面就需要自己慢慢完善了。

## 8、运行博客框架
运行方法和步骤5是一样的，只是我在本地运行获取到的主题框架时遇到了报错

``` python
$ cd /Users/liufangting/my_git/echo-music.github.io
$ sudo jekyll serve         
Traceback (most recent call last):
        10: from /usr/local/bin/jekyll:23:in `<main>'
         9: from /usr/local/bin/jekyll:23:in `load'
         8: from /usr/local/lib/ruby/gems/2.5.0/gems/jekyll-3.7.0/exe/jekyll:11:in `<top (required)>'
         7: from /usr/local/lib/ruby/gems/2.5.0/gems/jekyll-3.7.0/lib/jekyll/plugin_manager.rb:50:in `require_from_bundler'
         6: from /usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.1/lib/bundler.rb:107:in `setup'
         5: from /usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:26:in `setup'
         4: from /usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:26:in `map'
         3: from /usr/local/Cellar/ruby/2.5.0/lib/ruby/2.5.0/forwardable.rb:229:in `each'
         2: from /usr/local/Cellar/ruby/2.5.0/lib/ruby/2.5.0/forwardable.rb:229:in `each'
         1: from /usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:31:in `block in setup'
/usr/local/lib/ruby/gems/2.5.0/gems/bundler-1.16.1/lib/bundler/runtime.rb:313:in `check_for_activated_spec!': You have already activated public_suffix 3.0.1, but your Gemfile requires public_suffix 2.0.5. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```

看提示大概是gem软件版本方面的问题，网上找到用bundle exec来启动的，试了下果然能成功
如果项目启动报错：缺啥插件下啥插件，提示 jekyll 版本不对可以使用 bundle update 来更新 
使用 sudo bundle exec jekyll serve

``` sh
$ bundle exec jekyll serve --watch
Configuration file: /Users/liufangting/my_git/echo-music.github.io/_config.yml
       Deprecation: The 'gems' configuration option has been renamed to 'plugins'. Please update your config file accordingly.
            Source: /Users/liufangting/my_git/echo-music.github.io
       Destination: /Users/liufangting/my_git/echo-music.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
    Liquid Warning: Liquid syntax error (line 2): Expected dotdot but found pipe in "{{(site.github.public_repositories | sort: 'stargazers_count') | reverse }}" in pages/open-source.md
                    done in 3.437 seconds.
 Auto-regeneration: enabled for '/Users/liufangting/my_git/echo-music.github.io'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

用浏览器打开http://127.0.0.1:4000，就可以在本地访问博客，可以一边调整一边对照浏览，像极是一种调试模式。

## 9、添加文章和格式（博客写作）
要发布的文章都放在_posts目录下面，按照格式"年-月-日-文章名.markdown"

在_posts下建立文件或者拷贝过来
```
2020-05-20-mac-jekyll-github-blog.md
```

文章的开头，需要参照默认模板template
``` python
---
layout: post
title: template page
categories: [cate1, cate2]
description: some word here
keywords: keyword1, keyword2
---
```
- title: 文章标题
- date:  显示日期
- description: 描述
- categories: 标签分类

更多详细请查阅[jekyll官网文档](https://www.jekyll.com.cn/)，文档相关漂亮的。

文章最好按markdown标准语法来，养成良好的习惯，这样能提升写博客的效率。

## 10、发布文章
&emsp;&emsp;使用 git commit 提交修改，然后用 git push 将修改推送到 github 服务器（服务器会自动编译），之后访问你的博客公网链接 https://username.github.io ，即可。

## 11、绑定域名
在终端ping自己的域名
```
$ ping echo-music.github.io
```
得到公网IP地址：
```
PING sni.github.map.fastly.net (151.101.229.147): 56 data bytes
```

在域名供应商的控制台，添加解析，两条 A 记录：
```
记录类型    主机记录    解析线路(运营商)   记录值
A           @           默认              151.101.229.147
A           www         默认              151.101.229.147
```
记录值填写刚才获得的ip地址，在博客根目录添加CNAME文件,并将你的域名写入:
```
echo "www.echo-music.com" > CNAME
```

将CNAME提交，待域名解析完成，就可以了（大概1分钟解析时间）。

## 参考资料
[每个人都应该有一个Jekyll博客](https://www.tuicool.com/articles/ruMVjyN)

[使用jekyll搭建blog](http://www.zorin.xin/%E5%8D%9A%E5%AE%A2%E6%8A%80%E6%9C%AF/2017/02/20/%E4%BD%BF%E7%94%A8jekyll%E6%90%AD%E5%BB%BAblog.html)

[Jekyll官网](https://www.jekyll.com.cn/)

[主题来源于码志](https://github.com/mzlogin/mzlogin.github.io)

## 后话
借助开源项目Jekyll+免费的Github平台，就可以搭建属于自己的高颜值博客。

无需数据库、评论功能，不需要不断的更新版本——只用关心你的博客内容，真是简单、省心、高效，非常Nice!

一个好的博客，更多美好的开始。
