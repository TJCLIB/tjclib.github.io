---
layout:     post
title:      CentOS 7 搭建 LNMP型Web服务器
subtitle:
date:       2017-01-16
author:     Airmole
header-img: img/post-bg-os-metro.jpg
catalog: true
tags:
    - CentOS
    - LNMP
    - Web服务器
---

# CentOS 7 搭建 LNMP型Web服务器
## 安装Apache、PHP、MySQL、连接Mysql数据库的包:
`yum -y install httpd php mysql mysql-server php-mysql`
## 安装Apache常用拓展包：
`yum -y install httpd-manual mod_ssl mod_perl mod_auth_mysql`
## 安装PHP常用拓展包：
`yum -y install php-gd php-xml php-mbstring php-ldap php-pear php-xmlrpc php-devel`
## 安装Mysql常用的拓展包:
`yum -y install mysql-connector-odbc mysql-devel libdbi-dbd-mysql`
## 配置Apache、Mysql开机启动：
```
chkconfig httpd on
chkconfig mysqld on
```
## 重启Apache、Mysql
```
/etc/init.d/httpd restart
/etc/init.d/mysqld restart
```
进入/var/www/html文件夹之后
`vim test.php`
然后按键盘的I键，会出现Insert操作提示的
输入php代码
```
<?php
echo "Hello";
```
然后按ESC键退出，输入:wq，保存退出，这是VI编辑器的简单使用
然后在浏览器访问，输入IP
http://IP/test.php
可以看见输出Hello!说明我们环境搭建成功了
需要注意的是,我们要去服务器的配置安全组这里配置一下

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4697920-5fba31b89d4be8c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
勾选默认安全组放通全部端口，因为这些系统才允许我们访问服务器
