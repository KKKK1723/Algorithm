# 螺旋矩阵



给你一个 `m` 行 `n` 列的矩阵 `matrix` ，请按照 **顺时针螺旋顺序** ，返回矩阵中的所有元素。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)

```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg)

```
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
```

 

**提示：**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 10`
- `-100 <= matrix[i][j] <= 100`



```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int>ans;
        bool vis[15][15];
        memset(vis,0,sizeof(vis));
        int sum=0;
        int dex=1;//右 下 左 上
        int xx=0,yy=0;
        while(1)
        {
            ans.emplace_back(matrix[xx][yy]);
            vis[xx][yy]=1;
            sum++;
            if(sum==matrix[0].size()*matrix.size())return ans;

            if(dex==1)
            {
                yy++;
                
                if(yy>=matrix[0].size()||vis[xx][yy])
                {
                    dex++;//往下
                    yy--;
                    xx++;
                }
            }
            else if(dex==2)
            {
                xx++;
                if(xx>=matrix.size()||vis[xx][yy])
                {
                    dex++;//往左
                    xx--;
                    yy--;
                }
            }
            else if(dex==3)
            {
                yy--;
                if(yy<0||vis[xx][yy])
                {
                    dex++;//往上
                    yy++;
                    xx--;
                }
            }
            else if(dex==4)
            {
                xx--;
                if(xx<0||vis[xx][yy])
                {
                    dex=1;//往右
                    xx++;
                    yy++;
                }
            }
        }

    }
};
```

