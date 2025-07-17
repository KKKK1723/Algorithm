# 搜索二维矩阵



给你一个满足下述两条属性的 `m x n` 整数矩阵：

- 每行中的整数从左到右按非严格递增顺序排列。
- 每行的第一个整数大于前一行的最后一个整数。

给你一个整数 `target` ，如果 `target` 在矩阵中，返回 `true` ；否则，返回 `false` 。

 

**示例 1：**



```
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
输出：true
```

**示例 2：**

![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/11/25/mat2.jpg)

```
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
输出：false
```

 

**提示：**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 100`
- `-104 <= matrix[i][j], target <= 104`



```c++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int n=matrix.size();
        int m=matrix[0].size();
        if(matrix[0][0]>target||matrix[n-1][m-1]<target)return false;

        int h=0;
        //找行
        int left=-1,right=n;
        while(left+1!=right)
        {
            int mid=(left+right)/2;
            if(matrix[mid][0]<=target)
            {
                left=mid;
            }
            else
            {
                right=mid;
            }
        }
        h=left;

        //找列
        left=-1;
        right=m;
        while(left+1!=right)
        {
            int mid=(left+right)/2;
            if(matrix[h][mid]<target)
            {
                left=mid;
            }
            else{
                right=mid;
            }
        }

        return right < m && matrix[h][right]==target;
    }
};
```

