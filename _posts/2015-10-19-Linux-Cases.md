---
layout: post
title:  "Linux 小技能Get√"
date:  2015-10-19 22:20
categories: "Linux"
---

* content
{:toc}


###Linux 中 `su` 命令认证失败
新安装的Linux系统，在使用`su`命令时，很可能出现`认证失败`的提示，是因为`root`用户默认是被锁定了，不允许登陆，此时需要重新设置密码才行。

	～$ sudo passwd root
	[sudo] password for username: 
	输入新的 UNIX 密码： 
	重新输入新的 UNIX 密码： 
	passwd：已成功更新密码
