---
title : lambda表达式
data : 2018-07-15 00:00:00
tags : 
- python
- 函数式编程
- cpp
---

lambda表达式是一行函数，是函数式编程的一种特性。

## python

lambda <参数>: 表达式
```python
>>> f = lambda a,b: a + b
>>> type(f)
#<type 'function'>
```
获取整除2的数字
```python
>>> list(filter(lambda x: x%2==0, range(10)))
#[0, 2, 4, 6, 8]
```
列表并行排序
```python
>>> list1 = [1,2,3,2,3];list2 = [9,4,3,5,6]
>>> data = zip(list1, list2)
>>> data = sorted(data)
>>> list1, list2 = map(lambda t: list(t), zip(*data))
```
## cpp
<!-- more -->
c++里的形式是这样的
[capture list] (parameter list) ->return type {function body}
### 示例
```cpp
#include <iostream>
#include <string>
#include <algorithm>
#include <vector>
using namespace std;

int main() {
    //call the func.
    auto f1 = []() { cout << "test" << endl; }; 
    f1();
    int y = 2;
    auto f2 = [y](int x) {
        cout << x + y << endl;
    };
    f2(4);
    //STL
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(i);
    }
    for_each(v.begin(), v.end(), [](int n) { 
        if (n % 2 == 0) {
            cout << n << " ";
        }
    });
    return 0;
}
```
