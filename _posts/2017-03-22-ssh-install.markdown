---
layout:     post
title:      "ssh免密登录(CentOs7)"	
subtitle:   "ssh"			
date:       2017-03-22 17:26:00
author:     "dove"
header-img: "img/_posts/ssh.jpg"  
header-mask: 0.3
catalog:    true
tags:
    - ssh
---

# ssh安装步骤
1.每台机器执行:ssh-keygen -t rsa

生成一堆id_rsa和id_rsa.pub文件

2.执行 cat ~/.ssh/id_rsa.pub >>~/.ssh/authorized_keys 将秘钥添加到authorized_keys文件中

3.chmod 600 ~/.ssh/authorized_keys 这条命令一定要执行，要不然默认的664依旧需要输入密码(被坑了2个小时)

4.scp authorized_keys zcy@slave1:~/.ssh/authorized_keys_from_master

5.cat authorized_keys_from_master  >>  authorized_keys

第4和第五步就是将各台机器的秘钥发到其他机器的authorized_keys文件中

留作备用方便查看