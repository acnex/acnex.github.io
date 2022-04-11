---
layout: post
title: CentOS 7 MySQL密码重置
date: 2021-07-24 20:23:00
author: 牧之
tags: 
subtitle:   ""
header-style: text
---




## 修改 MySQL 配置文件以跳过密码登录

```sh
# vim /etc/my.cnf 
```

添加`skip-grant-tables`;

![98204-dhf64l3raec.png](https://blog.cseve.com/usr/uploads/2021/07/165151714.png)

## 重启 MySQL 服务

```sh
# systemctl restart mysqld.service
```
## 登录修改

```sh
[root@cvm-3ibcdh728a225 html]# mysql -u root 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.34 MySQL Community Server (GPL)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> USE mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set authentication_string='your-new-passwd' where user='root';
Query OK, 1 row affected (0.02 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> flush privileges ; 
Query OK, 0 rows affected (0.02 sec)

mysql> quit
Bye
```
## 将设置文件改回

```sh
# vim /etc/my.cnf 
```
## 重启 MySQL

```sh
# systemctl restart mysqld.service
```
修改完成。
