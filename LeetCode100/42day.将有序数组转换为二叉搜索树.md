# 108. 将有序数组转换为二叉搜索树
 
给你一个整数数组 nums ，其中元素已经按 升序 排列，请你将其转换为一棵 平衡 二叉搜索树。  

 

# 示例 1：    
![image](https://github.com/user-attachments/assets/53512a84-34ff-4cdc-9e7e-d1c692695897)  


输入：nums = [-10,-3,0,5,9]  
输出：[0,-3,9,-10,null,5]  
解释：[0,-10,5,null,-3,null,9] 也将被视为正确答案：  
![image](https://github.com/user-attachments/assets/e01daa94-4b9d-42da-9932-7aab0317ad2d)  


# 示例 2：  
![image](https://github.com/user-attachments/assets/eff0112b-61c1-43e9-b6a9-87a90a7e6f3a)  


输入：nums = [1,3]  
输出：[3,1]  
解释：[1,null,3] 和 [3,1] 都是高度平衡二叉搜索树。  
 

# 提示：  

1 <= nums.length <= 104  
-104 <= nums[i] <= 104  
nums 按 严格递增 顺序排列  

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return phtree(nums,0,nums.size()-1);
    }

    TreeNode* phtree(vector<int>&nums,int left,int right)
    {
        if(left>right)return nullptr;

        int mid=(left+right)/2;
        TreeNode* tmp=new TreeNode(nums[mid]);

        tmp->left=phtree(nums,left,mid-1);
        tmp->right=phtree(nums,mid+1,right);

        return tmp;
    }
};

```
