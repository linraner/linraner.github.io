---
title: Git问题：Everything up-to-date解决
date: 2017-11-04 12:39:28
tags: 
- git
---
push代码时遇到提示：``Everything up-to-date``,无法push代码
原因是git提交改动到缓存，要push的时候不会将本地所有的分支都push掉，所以出现这个问题。我们应该告诉git提交哪个分支。
## 解决
在[stackoverflow](https://stackoverflow.com/questions/2936652/git-push-wont-do-anything-everything-up-to-date)有解决方案

### 创建分支
```
$ git branch newbranch
#查看分支
$ git branch
```
### 切换分支
```
$ git checkout newbranch
```
<!-- more -->
### 改动提交到新的分支
```
$ git add .
$ git commit -a
```
### 合并到master
```
$ git merge newbranch
#查看冲突
$ git diff
```
### push代码
```
$ git push -u origin master
```
### 删除分支
```
$ git branch -D newbranch
```
* 删除合并部分大写D改为小写d




