# 搜索二维矩阵 II  
## 编写一个高效的算法来搜索 m x n 矩阵 matrix 中的一个目标值 target 。该矩阵具有以下特性：  

每行的元素从左到右升序排列  
每列的元素从上到下升序排列  



## 示例 1：  
![image](https://github.com/user-attachments/assets/41eeef63-a005-4ccb-bcb8-6361afc8f450)  

输入：matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5  
输出：true  


## 示例 2：  
![image](https://github.com/user-attachments/assets/aafab125-0125-43df-ac44-87615ea95020)  
输入：matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20  
输出：false  


```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int n=matrix.size();
        int m=matrix[0].size();
        bool end=false;
        
        for(int i=0;i<n;i++)
        {
            if(matrix[i][0]>target)break;
            int l=-1;
            int r=m;
            while(l+1!=r)
            {
                int mid=(l+r)/2;
                if(matrix[i][mid]<target)
                {
                    l=mid;
                }
                else
                {
                    r=mid;
                }
            }

            if(r!=m)
            {
                if(matrix[i][r]==target)end=true;
            }

            if(end)break;
        }



        return end;
    }
};

```
