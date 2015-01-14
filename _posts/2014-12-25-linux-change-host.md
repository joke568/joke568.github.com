---
layout: post
title: 'linux搬家笔记使用wget命令'
---
一，数据库
先备份数据库

```mysql
mysql -uroot -p123456 test > test.sql
```

二，从目标站下载文件

```linux
wget -nH -m --ftp-user=your_username --ftp-password=your_password ftp://your_ftp_host/*
```

说明

解释：
-nH：不创建以主机名命名的目录。
–cut-dirs：希望去掉原来的目录层数，从根目录开始计算。如果想完全保留FTP原有的目录结构，则不要加该参数。
-m：下载所有子目录并且保留目录结构。
–ftp-user：FTP用户名
–ftp-password：FTP密码
ftp://*.*.*.*/*：FTP主机地址。最后可以跟目录名来下载指定目录。

例：下载test目录下的所有文件

```linux
wget -nH -m --ftp-user=root --ftp-password=123456 ftp://192.168.1.1/test
```
