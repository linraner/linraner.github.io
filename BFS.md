---
title: BFS
date: 2018-04-01 18:16:21
tags: 
- acm
- 图论
- algorithm
---
## 入门

### 迷宫问题（最短路径）

### INPUT:
```
5 5
SXXXX
...XX
.X...
..XXX
....G
```
```
6 6

......
.S..X.
XXX...
....X.
.X..XX
.GX...
```
### OUPUT:
```
8
10
```
### 代码
<!-- more -->
```cpp
#include <iostream>
#include <queue>
using namespace std;
const int INF = 100000007;
const int mx = 1007;
typedef pair<int, int> P;

char maze[mx][mx];//地图
int n, m;
int sx, sy;//开始坐标 
int gx, gy;//结束坐标 

int d[mx][mx];//到各个位置的最短距离数组 

int dx[4] = {1,0,-1,0}, dy[4] = {0,1,0,-1};//移动向量 
//（sx,sy)---->(gx,gy)最短路径
//无法到达就是 INF 
int bfs(){
	queue<P> que;
	//初始化所有位置为INF 
	for(int i=0;i<n;i++){
		for(int j=0;j<m;j++){
			d[i][j]=INF;
		}
	}
	//放入起点 
	que.push(P(sx,sy));
	d[sx][sy]=0;
	//队列不为空一直执行 
	while(que.size()){
		//取出队列前端元素 
		P p=que.front();
		que.pop();
		//取出为终点结束搜索 
		if(p.first==gx&&p.second==gy) break;
		//4个方向的移动 
		for(int i=0;i<4;i++){
			//移动之后的位置 
			int nx=p.first+dx[i], ny=p.second+dy[i];
			//判断是否访问过 
			if(0<=nx&&nx<n&&0<=ny&&ny<m&&d[nx][ny]==INF&&maze[nx][ny]!='X'){
				que.push(P(nx,ny));//放入队列， 并到该位置的距离+1 
				d[nx][ny]=d[p.first][p.second]+1;
			}
		}
	}
	return d[gx][gy];
}

void solve(){
	int ans=bfs();
	cout << ans;
}
int main() {
	cin>>n>>m;
	for(int i=0;i<n;i++){
		scanf("%s",maze[i]);
		for(int j=0;j<m;j++){
			if(maze[i][j]=='S'){
				sx=i;sy=j;
			}
			if(maze[i][j]=='G'){
				gx=i;gy=j;
			}
		}
	}

	solve();
	return 0;
} 
```