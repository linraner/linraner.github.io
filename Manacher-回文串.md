---
title : Manacher算法-最长回文串
data : 2018-11-15 00:00:00
tags : 
- algorithm
- Java
- String
---
-----------------
## 题目

求解字符串最长回文串。

leetcode: [最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

## 样例
### Input
```
121
1
daccbba
bb
```

### Output
```
121
1
accbba
bb
```

`Manacher`算法，时间复杂度O(n), 空间复杂度O(1)。
### 步骤

先对s串处理转换为奇数长度的串。
```
s = "12212321"
==>
S # 1 # 2 # 2 # 1 # 2 # 3 # 2 # 1 #
P 1 2 1 2 5 2 1 4 1 2 1 6 1 2 1 2 1
```
p[i]表示记录以字符S[i]为中心的最长回文子串向左或向右扩张的长度（包括S[i]）。
即以i为原点的最大回文半径。

Manacher算法增加两个辅助变量id和mx。

id代表当前“已经匹配完毕的结尾最远的回文串”中心为s的第ID位。

mx = p[i] + id代表当前“已经匹配完毕的结尾最远的回文串”到达了s的第Mx位。

最长回文子串长度 = p[i] - 1 = 5。

2*id - i是i关于id的对称点

<!-- more -->
故p[i] = min(p[2*id-i], mx-i)

主要代码：

```c++
//对s进行修改
...
for (i = 1; i < s.length()-1; i++) 
{
    p[i] = mx > i ? min(p[2 * id - i], mx - i) : 1;
    while (s[i + p[i]] == s[i - p[i]]) 
        p[i]++;
    if (i + p[i] > mx) 
    {
        mx = i + p[i];
        id = i;
    }
}
...
// 求结果串
```

ac代码：

```java
ipublic class Main {

    public static void main(String[] args) throws InterruptedException {
        String s = "12212321";
    }

}
class Solution {
    private static String preProcess(String s) {
        int n = s.length();
        if (n == 0) {
            return "^$";
        }
        StringBuilder ret = new StringBuilder("^");
        for (int i = 0; i < n; i++)
            ret.append("#").append(s.charAt(i));
        ret.append("#$");
        return ret.toString();
    }

    public String longestPalindrome(String s) {
        String t = s;
        s = preProcess(s);
        int n = s.length();
        int[] p = new int[n];
        int mx = 0, id = 0;
        for (int i = 1; i < n - 1; i++) {
            p[i] = (mx > i) ? Math.min(p[2 * id - i], mx - i) : 1;
            while (s.charAt(i + p[i]) == s.charAt(i - p[i])) {
                p[i]++;
            }
            if (i + p[i] > mx) {
                mx = i + p[i];
                id = i;
            }
        }
        int maxLen = 0;
        int centerIndex = 0;
        for (int i = 1; i < p.length - 1; i++) {
            if (p[i] > maxLen) {
                maxLen = p[i];
                centerIndex = i;
            }
        }
        int start = (centerIndex - maxLen) / 2; 
        return t.substring(start, start + maxLen - 1);
    }

}
```

## 参考
[Manacher算法](https://segmentfault.com/a/1190000008484167)