---
title: Windows10 WIFI 热点问题
date: 2018-05-08 17:51:53
tags: 
- windows10
---

win10玄学bug之一

解决方案 ： 

命令行输入
```shell
$ netsh wlan set hostednetwork mode=allow ssid=NAME key=PASSWORD
$ netsh wlan start hostednetwork
```
然后在网络适配器的本地连接->属性->共享->设置共享刚才设置的WIFI热点