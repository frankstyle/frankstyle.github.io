---
layout: post
title:  "Ubuntu 下NodeJS 安装指南"
date:  2015-10-18 3:46
categories: "NodeJS"
---

* content
{:toc}

##安装流程

Ubuntu-14.04下通过命令

>`sudo apt-get install nodejs`

安装的`Nodejs`版本比较低，不太实用，还只能通过`nodejs comm`，命令来执行，所以不推荐此种安装方式。

干货链接：[NodeJS 开源包地址](http://nodejs.org/dist/)，目前提供如下两种方式安装`NodeJs`

###绿色非安装版
进入[NodeJs官网](http://nodejs.org/dist/)，选择适合的版本（如：`node-v0.12.7-linux-x64.tar.gz`），解压

>`tar -zxvf node-v0.12.7-linux-x64.tar.gz -C /opt/`

修改`/ect/profile`文件，设置`NodeJs`环境变量

>`sudo gedit /ect/profile`

在文件末尾处增加下面代码，保存后重新打开终端查看`node -v`是否生效。

>`export PATH=$PATH:/opt/nodejs/bin`


###编译后Install

选择合适的版本进行编译操作（如：`node-v0.12.3.tar.gz`），解压缩，准备编译

>`wget http://nodejs.org/dist/v0.12.3/node-v0.12.3.tar.gz`

	aptitude install gcc build-essential g++ libssl-dev apache2-utils 
	configure –prefix=/opt/
	make && make install

参考地址：[Ubuntu15.04编译安装nodejsV0.12.3](http://www.bubuko.com/infodetail-821876.html)，是否成功待实践。。。


###升级NodeJs
NodeJs在CGW的淫威下，升级一直不成功，设置PPA时好时坏，都不能好好的玩耍了，说多了都是泪
