---
title: 清除提交到github上的账号密码
date: 2018-11-01 00:00:00
tags: 
- git
---
----------
## 一、删库
。。。。
## 二、使用BFG Repo-Cleaner
地址： [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)
### 简单使用
```
#克隆副本
git clone --mirror git://example.com/example.git
#清理分支
java -jar bfg-1.13.0.jar --replace-text pwd.txt example.git
cd example.git & git reflog expire --expire=now --all && git gc --prune=now --aggressive & git push
```
### git 取消对某个文件的track
.gitignore无法对已经track的文件忽略
```git
git rm --cached example.files
git commit
git push
```
