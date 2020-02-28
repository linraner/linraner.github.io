---
title: 初学使用Git
date: 2017-10-24 13:27:03
tags: 
- git
---
## Git使用规范流程
Git是一个源码管理系统
我采取ThoughtBot的Git使用规范流程

### 第一步：新建分支
每次开发新功能，都应该新建一个单独的分支。
```
#获取主干最新代码
$ git checkout master
$ git pull

#新建开发分支
$ git checkout -b afeature
```
### 第二步：提交分支commit
<!-- more -->
分支修改后，提交commit
```
#all为保存所有变化(包括新建、修改和删除)
$ git add --all
#查看发生变动的文件。
$ git status
#verbose会列出diff的结果
$ git commit --verbose
```
* diff是Unix系统的一个很重要的工具程序，具体见：[读懂diff - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2012/08/how_to_read_diff.html)

### 第三步：撰写提交信息
提交commit时，必须给出完整扼要的提交信息。以下是一个范本：
```
Persent-tense summary under 50 characters
*More information about commit(under 72 characters)
*More information about commit(under 72 characters)
http://project.management-system.com/ticket/123
```
第一行是不超过50个字的提要，然后空一行，罗列出改动原因、主要变动、需要注意的问题。最后，提供对应的网址。
### 第四步：与主干同步
```
$ git fetch orgin
$ git rebase orgin/master
```
### 第五步：合并commit
分支开发完成后，很可能有一堆commit，但是合并到主干的时候，往往希望只有一个(或最多两三个) commit，这样不仅清晰，也容易管理。
```
$ git rebase -i origin/master
```
* 具体参考：[Git 使用规范流程](http://www.ruanyifeng.com/blog/2015/08/git-use-process.html)

### 第六步：推送到远程仓库
合并commit，推送当前分支到远程仓库。
```
$ git push --force origin myfeature
```
### 第七步：发出Pull Request
提交到远程仓库以后，就可以发出Pull Request 到master 分支，然后请求别人进行代码review，确认可以合并到master。
## Git常用操作
![](http://oxqn1kqf7.bkt.clouddn.com/17-10-26/83204462.jpg)

