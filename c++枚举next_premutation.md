---
title: c++枚举next_premutation
date: 2018-05-28 10:39:53
tags:
- acm
- c++
---

### 平均复杂度即为O(n)

* next_permutation()    会改变区间[begin,end)内的元素次序，使它们符合“下一个排列次序”；

* prev_permutation()    会改变区间[begin,end)内的元素次序，使它们符合“上一个排列次序”；


## 示例
<!-- more -->
```c++
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;
void f(vector<int> v){
	for(int i=0;i<v.size();i++){
		cout<<v[i]<<" ";
	}
	cout<<endl;
}
int main() {
	
	vector<int> v;
	v.push_back(1);
	v.push_back(3);
	v.push_back(2);
	cout<<"原排列 ： ";
	f(v); 
	for(int i=0;i<10;i++){
		next_permutation(v.begin(),v.end());//升序序列  或者下一个排列次序 按照字典序生成下一个序列 
		f(v);
	}

	//for(int i=0;i<5;i++){
	//	prev_permutation(v.begin(),v.end());//降序 
	//	f(v);
	//} 
	return 0;
}
```





