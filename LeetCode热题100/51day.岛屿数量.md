# 200. 岛屿数量



给你一个由 `'1'`（陆地）和 `'0'`（水）组成的的二维网格，请你计算网格中岛屿的数量。

岛屿总是被水包围，并且每座岛屿只能由水平方向和/或竖直方向上相邻的陆地连接形成。

此外，你可以假设该网格的四条边均被水包围。

 

**示例 1：**

```
输入：grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
输出：1
```

**示例 2：**

```
输入：grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
输出：3
```

 

**提示：**

- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 300`
- `grid[i][j]` 的值为 `'0'` 或 `'1'`



```c++

class Solution {
private:
    int ans,n,m;
    queue<pair<int,int> >q;
    int dx[4];
    int dy[4];
    bool vis[305][305];
public:
    int numIslands(vector<vector<char>>& grid) {
        ans=0;
        n=grid.size();//行
        m=grid[0].size();//列
        memset(vis,0,sizeof(vis));
        dx[0]=-1;dx[1]=1;dx[2]=0;dx[3]=0;
        dy[0]=0;dy[1]=0;dy[2]=-1;dy[3]=1;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(vis[i][j])continue;
                if(grid[i][j]=='1')
                {
                    bfs(i,j,grid);
                    ans++;
                }
            }
        }
        return ans;
    }

    void bfs(int x,int y,vector<vector<char>>& grid)
    {
        q.push({x,y});
        vis[x][y]=1;
        while(!q.empty())
        {
            auto t=q.front();
            q.pop();
            for(int i=0;i<4;i++)
            {
                int xx=t.first+dx[i];
                int yy=t.second+dy[i];
                if(xx<0||xx>=n||yy<0||yy>=m)continue;
                if(grid[xx][yy]!='1')continue;
                if(vis[xx][yy])continue;

                q.push({xx,yy});
                vis[xx][yy]=1;
            }
        }
    }
};
```

