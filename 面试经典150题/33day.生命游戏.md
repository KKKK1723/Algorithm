# 生命游戏



给定一个包含 `m × n` 个格子的面板，每一个格子都可以看成是一个细胞。每个细胞都具有一个初始状态： `1` 即为 **活细胞** （live），或 `0` 即为 **死细胞** （dead）。每个细胞与其八个相邻位置（水平，垂直，对角线）的细胞都遵循以下四条生存定律：

1. 如果活细胞周围八个位置的活细胞数少于两个，则该位置活细胞死亡；
2. 如果活细胞周围八个位置有两个或三个活细胞，则该位置活细胞仍然存活；
3. 如果活细胞周围八个位置有超过三个活细胞，则该位置活细胞死亡；
4. 如果死细胞周围正好有三个活细胞，则该位置死细胞复活；

下一个状态是通过将上述规则同时应用于当前状态下的每个细胞所形成的，其中细胞的出生和死亡是 **同时** 发生的。给你 `m x n` 网格面板 `board` 的当前状态，返回下一个状态。

给定当前 `board` 的状态，**更新** `board` 到下一个状态。

**注意** 你不需要返回任何东西。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/12/26/grid1.jpg)

```
输入：board = [[0,1,0],[0,0,1],[1,1,1],[0,0,0]]
输出：[[0,0,0],[1,0,1],[0,1,1],[0,1,0]]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/12/26/grid2.jpg)

```
输入：board = [[1,1],[1,0]]
输出：[[1,1],[1,1]]
```

 

**提示：**

- `m == board.length`
- `n == board[i].length`
- `1 <= m, n <= 25`
- `board[i][j]` 为 `0` 或 `1`

 



```c++
class Solution {
public:
    void gameOfLife(vector<vector<int>>& board) {
        int sum[30][30];
        memset(sum,0,sizeof(sum));
        int n=board.size();
        int m=board[0].size();
        int dx[8]={-1,1,0,0,-1,-1,1,1};
        int dy[8]={0,0,-1,1,-1,1,-1,1};
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                for(int k=0;k<8;k++)
                {
                    int xx=i+dx[k];
                    int yy=j+dy[k];
                    if(xx<0||xx>=n||yy<0||yy>=m)continue;
                    if(board[i][j]==1)
                    {
                        sum[xx][yy]++;
                    }
                    
                }
            }
        }

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(board[i][j]==1)
                {
                    if(sum[i][j]>3||sum[i][j]<2)board[i][j]=0;
                }
                else
                {
                    if(sum[i][j]==3)board[i][j]=1;
                }
            }
        }
    }
};
```

