---
layout: post
title:  "Ubuntu 下Ruby 2.0 以上版本安装指南"
date:  2015-10-18 3:46
categories: "Ruby"
tags: Ruby
excerpt: 安装 Ruby 的菜鸟指南

---

* content
{:toc}

### 安装流程

干货链接：[StackOverFlow：How to install Ruby 2 on Ubuntu without RVM](http://stackoverflow.com/questions/18490591/how-to-install-ruby-2-on-ubuntu-without-rvm)，推荐答案中有对应的安装方式。如果想获得更多的版本，可以直接访问[Ruby开源地址](http://ftp.ruby-lang.org/pub/ruby/)，选择对应的版本，建议通过编译安装。

	apt-get -y update
	apt-get -y install build-essential zlib1g-dev libssl-dev libreadline6 libreadline6-dev libyaml-dev
	cd /tmp
	wget http://ftp.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p451.tar.gz
	tar -xvzf ruby-2.0.0-p451.tar.gz
	cd ruby-2.0.0-p451/
	./configure --prefix=/usr/local
	make
	make install

>`./configure --prefix=/usr/local` configure是可执行文件，配置源码的编译环境  --prefix=/usr/local 是指定文件安装目录。

### 异常预警
某些Ruby版本在进行`make`或`make install`时，会出现`Function undeclared`错误，错误详情：

	readline.c:1977:26: error: 'Function' undeclared (first use in this function)
	    rl_pre_input_hook = (Function *)readline_pre_input_hook;
                          ^
	readline.c:1977:26: note: each undeclared identifier is reported only once for each function it appears in
	readline.c:1977:36: error: expected expression before ‘)’ token
	     rl_pre_input_hook = (Function *)readline_pre_input_hook;

StackOverFlow上也有对应的解答：[compile Ruby 2.0 errors without rvm or rbenv , readline.c:1886:26: error: 'Function' undeclared (first use in this function)](http://stackoverflow.com/questions/23488790/compile-ruby-2-0-errors-without-rvm-or-rbenv-readline-c188626-error-func)

### 解决方案
当出现`Function undeclared`时，将Ruby中的`ext/readline/readline.c`文件第1977行：

	rl_pre_input_hook = (Function *)readline_pre_input_hook;

替换为：

	rl_pre_input_hook = (rl_hook_func_t *)readline_pre_input_hook;

重新编译、安装即可，若还有问题，请自行[StackOverFlow](http://stackoverflow.com/)。

