# 48. 旋转图像  

给定一个 n × n 的二维矩阵 matrix 表示一个图像。请你将图像顺时针旋转 90 度。  

你必须在 原地 旋转图像，这意味着你需要直接修改输入的二维矩阵。请不要 使用另一个矩阵来旋转图像。  

 

## 示例 1：
![image](https://github.com/user-attachments/assets/9ebe7439-fe12-4ff0-a683-4bcaa5684be4)  

输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]  
输出：[[7,4,1],[8,5,2],[9,6,3]]  


## 示例 2：  
![image](https://github.com/user-attachments/assets/2fb8112c-0680-4d73-ac1f-6c9cb8b20c71)  

输入：matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]  
输出：[[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]  
 

## 提示：  

n == matrix.length == matrix[i].length  
1 <= n <= 20  
-1000 <= matrix[i][j] <= 1000  


```
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        for (int i = 0; i < n / 2; ++i) {
            for (int j = 0; j < (n + 1) / 2; ++j) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[n - j - 1][i];
                matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1];
                matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1];
                matrix[j][n - i - 1] = temp;
            }
        }
    }
};


```
