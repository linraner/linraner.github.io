---
title: django链接MySQL问题
date: 2018-6-21 12:00:00
tags: 
- skill
- django
- mysql
---
### 错误
```
（django.db.utils.OperationalError: (1045, "Access denied for user 'root'@'localhost' (using password: NO)")）
```
### 环境：
* Django2.0 
* MySQL8.0.11

<!-- more -->
Mysql 8.0 的部分语法，密码的加密方式发生了改变，在8.0 中的用户密码采用的是cha2 加密方法, 从而密码认证错误。

### 解决:

```mysql
$ mysql -u root -p
mysql> use mysql;
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; 
```
