---
title: DFS
date: 2018-04-01 18:15:02
tags:
- acm
- 图论
---
## 入门
### 求连通块
### INPUT :
```
1 1
*
3 5
*@*@*
**@**
*@*@*
1 8
@@****@*
5 5 
****@
*@@*@
*@**@
@@@*@
@@**@
0 0
```
### OUTPUT :
```
0
1
2
2
```
### 代码
<!-- more -->
```cpp
#include <iostream>
using namespace std;
const int mx = 10007;
int n, m;
char field[mx][mx];//地图 
void dfs(int x, int y){
	field[x][y] = '*';//替换现在位置 
	//遍历8个方向 
	for(int dx=-1;dx<=1;dx++){
		for(int dy=-1;dy<=1;dy++){
			int nx=x+dx, ny=y+dy;
			if(0<=nx&&nx<n&&0<=ny&&ny<m&&field[nx][ny]=='@')
				dfs(nx,ny);
		}
	}
	
	return ;
}
 
void solve(){
	int ans=0;
	for(int i=0;i<n;i++){
		for(int j=0;j<m;j++){
			//从@处开始遍历 
			if(field[i][j]=='@'){
				dfs(i,j);
				ans++;
			}	
		}
	}
	cout<<ans;
}
int main() {
	cin>>n>>m;
	for(int i=0;i<n;i++){
		scanf("%s",field[i]);
	}	
	solve();
	return 0;
} 
```