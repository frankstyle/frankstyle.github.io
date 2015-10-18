---
layout: post
title:  "使用GitHub Pages 搭建个人博客（一）——创建个人主页"
date:  2015-10-17 17:46
categories: "GitHub-Pages"
---

* content
{:toc}

##前言
之前一直想用GitHub Pages 搭建自己的博客乐园，中间断断续续查阅了相关的资料，拖到现在才实施。刚好最近又在学习Git相关的知识，顺便撸一把Markdown。从现在开始，慢慢妆点小窝......


##GitHub 创建个人主页项目
在使用GitHub Pages搭建博客时，需要有GitHub账号才行，登陆[GitHub](https://github.com/) ,右侧点击`+New repository`创建一个新的项目仓库，针对`Repository name`，GitHub Pages 有特殊的要求：必须使用`username.github.io`作为仓库的名字！
创建完项目仓库后，就可以使用`http(s)://<username>.github.io`来访问啦，一个简单的个人博客模型出来了。详细内容请链接 [GitHub Pages Help](https://help.github.com/categories/github-pages-basics/)，里面有详细的说明。

##GitHub Pages 域名绑定
GitHub Pages 提供了域名绑定的功能，可以通过访问自己的域名来跳转到个人主页。目前有两种方式设置个性域名，绑定到一级域名和绑定二级域名，两种绑定方式有细微差别。
###使用Git 克隆仓库到本地

推荐使用Mac或Linux系统来进行相关实践，小渣使用的是Ubuntu-14.04系统来搭建的。

####安装Git
`Ctrl+Alt+T`打开终端

>` sudo apt-get install git`

在[Github](https://github.com)页面中找到刚才创建的个人主页仓库的`Https`地址（如：https://github.com/frankstyle/frankstyle.github.io.git），在终端进行`Clone`操作：`git clone https://github.com/frankstyle/frankstyle.github.io.git`。
期间如果提示设置`global user.emal`和`global user.name`.按照对应的提示设置即可，然后继续克隆。

####绑定域名
例如小渣域名`http://frankstyle.com`，一级域名就是 `frankstyle.com`，二级则可以有多个，如：`xxx.frankstyle.com`。

> `cd <username>.github.io`

进入仓库根目录，创建`CNAME`文件。注意此文件没有后缀修饰。编辑`CNAME`文件，输入需要绑定的域名（如：`frankstyle.com`，注意没有www前缀，只写域名）然后保存。提交CNMA文件到GitHub远程仓库:

> `git add CNAME`
> `git commit -m "info"`
> `git push`

GitHub端设置好后还要配置域名服务器，使其进行解析跳转。进入域名管理（万网等）页面。

- 绑定到一级域名
	
> 绑定到一级域名时，只需设置A类型记录即可,几分钟后即可生效，访问地址如：[http:frankstyle.com](http://frankstyle.com)
![enter image description here](http://7xnlje.com1.z0.glb.clouddn.com/frankcname1.png)
对应的IP地址为GitHub Pages提供的固定IP，[查看IP Address](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/)

- 绑定到二级域名

> 绑定二级域名时，需要设置cname纪录目前实验过,详情请参考[GitHub Help](https://help.github.com/articles/tips-for-configuring-a-cname-record-with-your-dns-provider/)


---------
干货链接：

 - [知乎：怎样做一个漂亮的 GitHub Pages 首页？](http://www.zhihu.com/question/20376047)

 - [一步步在GitHub上创建博客主页](http://www.pchou.info/web-build/2014/07/04/build-github-blog-page-08.html)

 - [一步步在GitHub上创建博客主页（一～七）](http://www.pchou.info/web-build/2013/01/05/build-github-blog-page-03.html)
 

