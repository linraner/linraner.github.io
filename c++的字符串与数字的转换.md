---
title : c++的字符串与数字的转换
data :  2018-3-16 12:22:12
tags :  
- 字符串
- acm
- c++ 
---
###  数字转字符串

```c++
#include <sstream>
double a = 123.456;
string s;
stringstream ss;
ss << a;
ss >> s;
ss.clear();
```

```c++
#include <map>
map<int, char> m;
for (int i = 0; i < 10; i++) {
	m[i] = i + '0';
}
```

```c++
#include <cstdio>
char str[10];
double a = 123.456;
sprintf(str, "%.3lf", a);
```

```c++
char str[10];
int a=175;
sprintf(str,"%x",a);//10进制转换成16进制，如果输出大写的字母是sprintf(str,"%X",a)
```

### 字符串转数字
<!-- more -->
```c++
#include <sstream>
string s = "123.456";
double a;
stringstream ss;
ss << s;
ss >> a;
ss.clear();
```

```c++
#include <map>
map<char, int> m;
for (int i = 0; i < 10; i++) {
    m[i+'0'] = i;
}
```

```c++
#include <cstdio>
char str[] = "123.456";
double a;
sscanf(str, "%lf", &a);
```

```c++
char str[]="AF";
int a;
sscanf(str,"%x",&a); //16进制转换成10进制
```

```c++
#include <cstdlib>
int a;float b;long c;
a=atoi("32");
b=atof("3.1415");
c=atol("567283");
printf ("%d\n%f\n%d\n",a,b,c);
```

