---
title: conda常用操作(windows)
date: 2017-10-28 10:22:46
tags:
- tools 
- skill
---

## 管理conda
### 验证安装
```
$ conda --version
```
命令参阅可以用: conda --help
### 将conda更新到最新
```
$ conda update conda
#有最新选择yes
Proceed ([y]/n)? y
```
<!-- more -->
## 管理环境
### 创建环境
```
$ conda create --name snowflakes biopython
#也可以指定python版本并安装Astroid和Babel
$ conda create --name snowflakes python3.5 astroid babel
```
使用biopython创建一个snowflakes的环境
* 不指定目录即为默认目录/envs

### 使用环境
```
$ activate newen
#切换回根目录
$ deactivate
```
### 显示安装过的环境
```
$ conda info --envs
```
![显示安装过的环境](http://oxqn1kqf7.bkt.clouddn.com/17-10-28/22089148.jpg)
括号显示为当前环境
![括号显示为当前环境](http://oxqn1kqf7.bkt.clouddn.com/17-10-28/43734134.jpg)
### 切换到另一个环境
```
$ activate another_environment
```
### 克隆删除环境
```
#克隆
$ conda create --name flowers --clone snowflakes
#删除
$ conda remove --name flowers --all
```
## 管理Python
### 检查可安装的python版本
```
$ conda search --full-name python
#列出包含python的所有包
$ conda search python
```
### 安装python3环境并不覆盖python2
```
$ conda create --name snackes pyhton=3
```
## 包管理
### 看安装的包和版本列表
```
$ conda list
```
### 查找、安装、删除
```
$ conda search beautifulsoup4
$ conda install --name snowflakes beautifulsoup4    #未指定位置安装在当前位置
$ conda remove --name snowflakes beautifulsoup4
```
### 从Anaconda.org安装包
```
$ conda install --channel https://conda.anaconda.org/pandas bottleneck
```

* **更多命令具体参考：**[Getting started](https://conda.io/docs/user-guide/tasks/view-command-line-help.html)
