---
layout: post
title:  "使用GitHub Pages 搭建个人博客（二）——Jekyll 环境搭建"
date:  2015-10-18 2:46
categories: "GitHub-Pages"
---

* content
{:toc}

##Jekyll模板选择

小渣的博客是使用GitHub Pages 配合 Jekyll 来搭建的，使用[Jekyll](http://jekyll.bootcss.com/) 能够将纯文本转化为静态网站和博客，同时也提供很多[漂亮的模板](http://jekyllthemes.org/)供博主们选择。
从[Jekyll模板](http://jekyllthemes.org/)选择适合自己的模板，可以直接点击`Download`下载`tar.gz`格式的压缩包，解压即可使用：

>`tar -zxvf package.tar.gz`

也可以直接点击`Homepage`查看模板仓库的位置（GitHub仓库），Clone其`https URL`到本地即可。

>`git clone https://github.com/xxx/xxx.git`

干货链接：[GitHub Pages 官网：Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages)

##安装Ruby

Jekyll本身基于Ruby开发，因此，如果要在本地构建一个测试环境需要具有Ruby的开发和运行环境，并且Ruby版本至少2.0。安装方法参照[Ruby安装指南](http://frankstyle.com/2015/10/18/Ruby-install/)，也可以参照[StackOverFlow：How to install Ruby 2 on Ubuntu without RVM](http://stackoverflow.com/questions/18490591/how-to-install-ruby-2-on-ubuntu-without-rvm)
高版本的Ruby自带Gem工具，无需重新安装Gem。


##安装Bundle

>Bundle用来来管理项目中所有gem依赖，该命令只能在一个含有Gemfile的目录下执行

通过命令来查看当前gem 配置的source源，由于CGW原因你懂的

>`gem sources -l`

执行命令安装bundle，如有需要，可以加上`sudo`提高权限。

>`gem install bundler`


###异常预警

在CGW的淫威下，`install`很可能会出现以下问题

	ERROR:  Could not find a valid gem 'bundler' (>= 0), here is why:
		Unable to download data from https://rubygems.org/ - Errno::ETIMEDOUT: Operation timed out - connect(2) (https://rubygems.org/latest_specs.4.8.gz)
	ERROR:  Possible alternatives: bundler

此时需要重新设置gem源，目前国内有较不错的源可用：[http://ruby.taobao.org/](http://ruby.taobao.org/)


###解决方案

使用新的gem源：`http://ruby.taobao.org/`
	
	gem sources --remove https://rubygems.org/
	gem sources -a http://ruby.taobao.org/
	gem sources -l
	*** CURRENT SOURCES ***
	http://ruby.taobao.org

请确保只有`ruby.taobao.org`，然后重新执行`install`操作。


##导入Jekyll博客模板

>将已下载好的博客模板文件夹内容复制到个人主页仓库中（根目录）,有些文件不必替换，如：`CNAME、README.md` 等。

##安装依赖包
在个人主页仓库根目录中新建名叫`Gemfile`的文件，注意此文件没有后缀修饰，文件内容：

	source 'http://ruby.taobao.org/'
	gem 'github-pages'

保存后执行`install`操作，安装Github Pages相关的依赖包，如有需要，可以`sudo`。

>`bundle install`

此时，Jekyll也一起被安装了，后面会执行Jekyll来启动本地服务。


##启动本地服务

在个人主页仓库根目录启动`Jekyll`服务：

>`jekyll server`

若启动成功启动，会出现类似如下界面

	frank@frank:~/myprojects/frankstyle.github.io$ jekyll server
	Configuration file: /home/frank/myprojects/frankstyle.github.io/_config.yml
            Source: /home/frank/myprojects/frankstyle.github.io
       Destination: /home/frank/myprojects/frankstyle.github.io/_site
      Generating... 
                    done.
	 Auto-regeneration: enabled for '/home/frank/myprojects/frankstyle.github.io'
	Configuration file: /home/frank/myprojects/frankstyle.github.io/_config.yml
    Server address: http://0.0.0.0:4000/
	  Server running... press ctrl-c to stop.

可以通过 [http://localhost:4000](http://localhost:4000)进行访问
jekyll  Could not find a JavaScript runtime

###异常预警

在启动`Jekyll`时，可能会出现`jekyll  Could not find a JavaScript runtime`的问题。这是因为Jekyll运行需要服务器支持，安装一个`NodeJS`即可。可以参照[NodeJs安装指南](#)
