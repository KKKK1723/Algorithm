# 73. 矩阵置零

给定一个 m x n 的矩阵，如果一个元素为 0 ，则将其所在行和列的所有元素都设为 0 。请使用 原地 算法  

 

## 示例 1：  

输入：matrix = [[1,1,1],[1,0,1],[1,1,1]]  
输出：[[1,0,1],[0,0,0],[1,0,1]]  


![image](https://github.com/user-attachments/assets/d7f6584b-76fc-4878-abe0-77517717b6dc)

## 示例 2：


输入：matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]  
输出：[[0,0,0,0],[0,4,5,0],[0,3,1,0]]  
![image](https://github.com/user-attachments/assets/e742c38a-0c2f-4c3e-9d8d-1213dcfdd4f5)

## 提示：

m == matrix.length  
n == matrix[0].length  
1 <= m, n <= 200  
-231 <= matrix[i][j] <= 231 - 1  



 ```
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int m = matrix.size();
        int n = matrix[0].size();
        bool vish[500],visl[500];

        memset(vish,0,sizeof(vish));
        memset(visl,0,sizeof(visl));

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (!matrix[i][j]) {
                    vish[i] = visl[j] = true;
                }
            }
        }
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (vish[i] || visl[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
};



```
