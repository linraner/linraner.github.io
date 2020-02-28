---
title: nothing added to commit but untracked files present解决方法
date: 2018-05-30 17:05:53
tags: 
- git
---

## 问题描述

```shell
$ git commit                                                         
On branch master                                                     
                                                                     
Initial commit                                                       
                                                                     
Untracked files:                                                     
        .gitignore                                                   
        Test/                                                        
        blogpost/                                                    
        manage.py                                                    
                                                                     
nothing added to commit but untracked files present                  
```

**文件被追踪，但是没有被添加git中**

## 解决
<!-- more -->
**git status 列出当前目录所有还没有被git管理的文件和被git管理且被修改但还未提交(git commit)的文件**

```shell
$ git add manage.py
$ git add blogpost\
$ git add Test\
$ git add .gitignore
```