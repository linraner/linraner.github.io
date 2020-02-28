---
title: 'c++ std::ios_base::sync_with_stdio 加速输入输出'
date: 2018-05-14 14:57:41
tags:
- acm
- c++
---
### ``static bool sync_with_stdio( bool sync = true ); ``
设置标准 C++ 流是否与标准 C 流在每次输入/输出操作后同步。

遇到cin TLE时可以用于取消cin同步, 取消之后不能和 scanf，sscanf, getchar, fgets 之类同用。

#### 测试
<!-- more -->
```c++
#include <iostream>
#include <cstdio>
 
int main() {
    std::ios::sync_with_stdio(false);
    std::cout << "a\n";
    std::printf("b\n");
    std::cout << "c\n";
}
```

#### 输出 （环境 g++5.4.0）

```c++
b
c
a
```
默认的情况下cin绑定的是cout，每次执行 << 操作符的时候都要调用flush，这样会增加IO负担。

```c++
    std::ios::sync_with_stdio(false);
    std::cin.tie(0);
```

参考一 ： http://zh.cppreference.com/w/cpp/io/ios_base/sync_with_stdio

参考二 ：http://www.hankcs.com/program/cpp/cin-tie-with-sync_with_stdio-acceleration-input-and-output.html