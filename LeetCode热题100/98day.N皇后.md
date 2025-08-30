# N 皇后



按照国际象棋的规则，皇后可以攻击与之处在同一行或同一列或同一斜线上的棋子。

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n×n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回所有不同的 **n 皇后问题** 的解决方案。

每一种解法包含一个不同的 **n 皇后问题** 的棋子放置方案，该方案中 `'Q'` 和 `'.'` 分别代表了皇后和空位。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

```
输入：n = 4
输出：[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

**示例 2：**

```
输入：n = 1
输出：[["Q"]]
```

 

**提示：**

- `1 <= n <= 9`



```c++
class Solution {
public:
    bool h[10], l[10], zx[20], yx[20]; 
    int ans;
    
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> res;
        vector<string> tmp(n, string(n, '.')); 
        ans = 0;
        memset(h, 0, sizeof(h));
        memset(l, 0, sizeof(l));
        memset(zx, 0, sizeof(zx));
        memset(yx, 0, sizeof(yx));
        
        dg(tmp, res, 0, n, ans);
        return res;
    }
    
    void dg(vector<string>& tmp, vector<vector<string>>& res, int now, int num, int& sum) {
        if (now == num) 
        {  
            res.emplace_back(tmp);
            return;
        }
        
        for (int i = 0; i < num; i++) {
            if (l[i]) continue;
            if (zx[now - i + num - 1] || yx[now + i]) continue;  
            
            tmp[now][i] = 'Q';
            l[i] = 1;
            zx[now - i + num - 1] = 1; 
            yx[now + i] = 1; 
            
            dg(tmp, res, now + 1, num, sum); 
            
            l[i] = 0;
            zx[now - i + num - 1] = 0;
            yx[now + i] = 0;
            tmp[now][i] = '.';
        }
    }
};
```

