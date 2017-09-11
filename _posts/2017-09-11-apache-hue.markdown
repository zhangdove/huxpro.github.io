---
layout:     post
title:      "hue安装"	
subtitle:   "apache hue"			
date:       2017-09-11 12:00:00
author:     "dove"
header-img: "img/avatar-hux-home.jpg"  
header-mask: 0.3
catalog:    true
tags:
    - hue
---
<前言:使用如下命令安装
<sudo yum install gcc
<sudo yum install gcc-c++
<sudo yum install libxml2-devel
<sudo yum install libxslt-devel
<sudo yum install cyrus-sasl-devel
<sudo yum install cyrus-sasl-gssapi
<sudo yum install mysql
<sudo yum install python-devel
<sudo yum install python-setuptools
<sudo yum install sqlite-devel
<sudo yum install ant
<sudo yum install cyrus-sasl-plain
<sudo yum install krb5-dev
<sudo yum install openldap-devel.x86_64
<sudo yum install gmp-devel.x86_64


# 1.配置hdfs-site.xml
	<property>
		 <name>dfs.webhdfs.enabled</name>
		 <value>true</value>
	</property>

# 2.配置core-site.xml
	<property>
		 <name>hadoop.proxyuser.hue.hosts</name>
		 <value>*</value>
	</property>
	 
	<property>
		 <name>hadoop.proxyuser.hue.groups</name>
		 <value>*</value>
	</property>
[安装其他参考](https://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.3.4/bk_installing_manually_book/content/configure_hdp_hue.html)


# 3.配置hive-site.xml
	<property>
		 <name>hive.server2.enable.doAs</name>
		 <value>true</value>
	</property>

# 下载
git clone https://github.com/cloudera/hue.git
cd hue
chmod 777 /disk/hue/hue-3.9.0/desktop/desktop.db
make apps
build/env/bin/hue runserver 0.0.0.0:8000

# hue.ini 配置如下  (这里只配置了hive的)
<http_host=192.168.139.128
<http_port=8888
<secret_key=adfhaoweasdnf2387erlnad9283=-=-123n2-34nd
<fs_defaultfs=hdfs://master:8020
<webhdfs_url=http://master:50070/webhdfs/v1
<hadoop_conf_dir=/disk/hadoop-2.6.4/etc/hadoop/
<resourcemanager_host=master
<resourcemanager_port=8032
<resourcemanager_api_url=http://Yarn_host_ip:8088
<submit_to=True
<hive_server_host=master
<hive_server_port=10000
<hive_conf_dir=/usr/hive-1.2.1/conf
<default_hdfs_superuser=dove
<[[database]]
<engine=sqlite3
<name=desktop/desktop.db