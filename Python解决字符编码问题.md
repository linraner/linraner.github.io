---
title: Python解决字符编码问题
date: 2018-05-05 22:33:02
tags:
- python
- skill
---
字符串分为unicode 和 str 两种类型

文本字符和二进制数据分别用 str 和 byte表示

```python
#系统默认编码设置为utf-8
>>> import sys
>>> sys.getdefultencoding
'utf-8'
>>> 
```

str 与 bytes 之间的转换可以用 encode 和从decode 
<!-- more -->
![](https://foofish.net/images/python3-str2.jpg)

```python
>>> s = "Python测试"
>>> s = s.encode()
>>> print(s)
b'Python\xe6\xb5\x8b\xe8\xaf\x95'
>>> s = s.decode()
>>> print(s)
'Python测试'
```
## base64
```python
>>> import base64
>>> s = "asdasd"
>>> s = base64.b64encode(s)
>>> print(s)
>>> s = base64.b64decode(s)
>>> print(s)
```
-------------------
参考 ： https://foofish.net/how-python3-handle-charset-encoding.html