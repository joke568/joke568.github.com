---
layout: post
title: 'linux的一键安装包'
---
经常会配置一些环境要用到的，大部分都是在命令行下面操作的。已经安装了好几个服务器了，非常的好用和稳定。[点击下载linux一键安装包](/files/sh-1.3.0.zip).

使用方法：

1，上传到/home文件夹里面，用WinSCP这个软件就可以。

2，进入到home，更改文件夹的权限。

```sh
cd /home

chmod –R 777 sh-1.3.0

cd sh-1.3.0

./install.sh
```
3,选择apache或者nginx，php,mysql等等，这里就不截图了。

4，安装完后查看账号信息

```sh

cat account.log

```

这里是经常要用到的一些命令

---------------------------

网站目录：/alidata/www
服务器软件目录：/alidata/server

Mysql 目录 /alidata/server/mysql

Php目录/alidata/server/php

 

选择了nginx 那么会有一个nginx 目录在 /alidata/server/nginx/

Nginx 配置文件在/alidata/server/nginx/conf

Nginx虚拟主机添加 你可以修改/alidata/server/nginx/conf/vhosts/phpwind.conf

 

选择了apache那么会有一个httpd 目录在 /alidata/server/httpd

apache 配置文件在/alidata/server/httpd/conf

apache虚拟主机添加 你可以修改/alidata/server/httpd/conf/vhosts/phpwind.conf


各个服务操作命令汇总：


nginx：

/etc/init.d/nginx start/stop/restart/reload)


apache:

/etc/init.d/httpd start/stop/restart/...


mysql:

/etc/init.d/mysqld  start/stop/restart/...


php-fpm:

/etc/init.d/php-fpm  start/stop/restart/...


ftp:

/etc/init.d/vsftpd  start/stop/restart/...

比如启动nginx：

/etc/init.d/nginx start

-------------------------
经常使用的两个liunx的命令

chmod -R 777 www         //遍历更改权限是777

chown -R www www         //遍历更改用户组为www www文件夹
