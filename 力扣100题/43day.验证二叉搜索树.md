# 98. 验证二叉搜索树  

给你一个二叉树的根节点 root ，判断其是否是一个有效的二叉搜索树。  

有效 二叉搜索树定义如下：  

节点的左子树只包含 小于 当前节点的数。  
节点的右子树只包含 大于 当前节点的数。  
所有左子树和右子树自身必须也是二叉搜索树。  
 

# 示例 1：  
![image](https://github.com/user-attachments/assets/47d39070-e924-41f3-97f1-84e939312e4e)  


输入：root = [2,1,3]  
输出：true    
# 示例 2：  
![image](https://github.com/user-attachments/assets/56ca84f1-f0d7-46de-8713-aa3623a88614)    


输入：root = [5,1,4,null,null,3,6]  
输出：false  
解释：根节点的值是 5 ，但是右子节点的值是 4 。   
 

提示：  

树中节点数目范围在[1, 104] 内  
-231 <= Node.val <= 231 - 1  

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
    bool isValidBST(TreeNode* root) {
        return check(root,LONG_MIN,LONG_MAX);
    }

    bool check(TreeNode* root,long long leftq,long long rightq)
    {
        if(root==nullptr)return true;

        if(root->val>=rightq||root->val<=leftq)return false;

        return (check(root->left,leftq,root->val)&&check(root->right,root->val,rightq));
    }
};

```
