# 腐烂的橘子



在给定的 `m x n` 网格 `grid` 中，每个单元格可以有以下三个值之一：

- 值 `0` 代表空单元格；
- 值 `1` 代表新鲜橘子；
- 值 `2` 代表腐烂的橘子。

每分钟，腐烂的橘子 **周围 4 个方向上相邻** 的新鲜橘子都会腐烂。

返回 *直到单元格中没有新鲜橘子为止所必须经过的最小分钟数。如果不可能，返回 `-1`* 。

 

**示例 1：**

**![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/16/oranges.png)**

```
输入：grid = [[2,1,1],[1,1,0],[0,1,1]]
输出：4
```

**示例 2：**

```
输入：grid = [[2,1,1],[0,1,1],[1,0,1]]
输出：-1
解释：左下角的橘子（第 2 行， 第 0 列）永远不会腐烂，因为腐烂只会发生在 4 个方向上。
```

**示例 3：**

```
输入：grid = [[0,2]]
输出：0
解释：因为 0 分钟时已经没有新鲜橘子了，所以答案就是 0 。
```

 

**提示：**

- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 10`
- `grid[i][j]` 仅为 `0`、`1` 或 `2`



```c++
class Solution {
private:
    queue<pair<int,int> >q;
    int dx[4],dy[4];
    int dis[11][11];//时间
    int maxtime,n,m;
    bool vis[11][11];
public:
    int orangesRotting(vector<vector<int>>& grid) {
        n=grid.size();//行
        m=grid[0].size();//列
        maxtime=0;
        memset(dis,0,sizeof(dis));
        memset(vis,0,sizeof(vis));
        dx[0]=-1;dx[1]=1;dx[2]=0;dx[3]=0;
        dy[0]=0;dy[1]=0;dy[2]=-1;dy[3]=1;

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(grid[i][j]==2)
                {
                    q.push({i,j});
                    vis[i][j]=1;
                }
            }
        }

        bfs(grid);

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(grid[i][j]==1&&vis[i][j]==0)
                {
                    return -1;
                }
            }
        }
        return maxtime;
    }

    void bfs(vector<vector<int>>& grid)
    {
        while(!q.empty())
        {
            auto t=q.front();
            q.pop();
            for(int i=0;i<4;i++)
            {
                int xx=t.first+dx[i];
                int yy=t.second+dy[i];
                if(xx<0||xx>=n||yy<0||yy>=m)continue;
                if(grid[xx][yy]==0||grid[xx][yy]==2)continue;
                if(vis[xx][yy])continue;

                q.push({xx,yy});
                vis[xx][yy]=1;
                dis[xx][yy]=dis[t.first][t.second]+1;
                maxtime=max(maxtime,dis[xx][yy]);
            }
        }
    }
};
```

