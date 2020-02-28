---
title: Ubuntu错误-Could not get lock /var/lib/dpkg/lock
date: 2018-05-15 17:45:02
tags:
- ubuntu
- skill
---

### 报错信息 

```shell
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

### 解决办法 
<!-- more -->
#### 查看运行的线程
```shell
ps -A | grep apt-get
# sudo kill processnumber
# 关闭apt进程
```
我的没有发现进程， 可能是上次运行安装或更新时没有正常完成造成的

#### 终端输入 
```shell
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```