---
layout:     post
title:      "ssh安装"	
subtitle:   "ssh install"			
date:       2017-3-22 17:26
author:     "dove"
header-img: "img/_posts/ssh.jpg"  
header-mask: 0.3
catalog:    true
tags:
    - hue
	- install
	
---



1. 每台机器执行:ssh-keygen -t rsa,生成一堆id_rsa和id_rsa.pub文件
1. 执行 cat ~/.ssh/id_rsa.pub >>~/.ssh/authorized_keys 将秘钥添加到authorized_keys文件中
1. chmod 600 ~/.ssh/authorized_keys 这条命令一定要执行，要不然默认的664依旧需要输入密码(被坑了2个小时)
1. scp authorized_keys zcy@slave1:~/.ssh/authorized_keys_from_master
1. cat authorized_keys_from_master  >>  authorized_keys

第4和第五步就是将各台机器的秘钥发到其他机器的`authorized_keys`文件中
留作备用方便查看
