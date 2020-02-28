---
title: scanf中的正则表达式
date: 2017-11-31 18:57:58
tags: 
- acm
- c++ 
---

#### **调用格式:** ``scanf("<格式化字符串>", <地址表>);``

一、为变量赋值时表示成功读取变量的个数, <格式化字符串>与<地址表>是严格匹配的

```cpp
scanf("%c %c", &a, &b); //函数返回值是2，并丢弃不想使用的空白符
scanf("%d,%d", &a, &b); //输入必须有逗号， 多个空格为一个空格
```

二、 ``%s`` 读取遇到空格停止读取，因此一般可以用fgets去读取字符串
<!-- more -->
```cpp
scanf("%[a-z]", &str);  //遇到不再a-z字符停止读取
scanf("666%[0-9]", &str);  //666开头并且在0-9字符读取，不是则停止
scanf("%[^\n]", &str);     //^表示求反集，即这句话不是回车一直开始读取
```

三、压缩输入：在格式码前加上*，则用户就可以告诉scanf()读这个域，但不把它赋予任何变量。

```cpp
scanf("%c%*c, &ch); 使用此方法可以在字符处理时吃掉多余的回车。
```

[更多正则表达式语言参考](https://docs.microsoft.com/zh-cn/dotnet/standard/base-types/regular-expression-language-quick-reference)


#### sscanf、scanf的一些示例

```cpp

```
