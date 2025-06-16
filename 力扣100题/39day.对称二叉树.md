# 101. 对称二叉树  

给你一个二叉树的根节点 root ， 检查它是否轴对称  
 

# 示例 1：  
![image](https://github.com/user-attachments/assets/f914302a-49e5-4dc4-8c22-e5adbfecf3f0)  


输入：root = [1,2,2,3,4,4,3]  
输出：true  
# 示例 2：  
![image](https://github.com/user-attachments/assets/c7f39da2-ce77-499a-b9a0-5c39a2df7ad2)  


输入：root = [1,2,2,null,3,null,3]  
输出：false  
 

# 提示：  

树中节点数目在范围 [1, 1000] 内  
-100 <= Node.val <= 100  

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

    bool pd(TreeNode* left,TreeNode* right)
    {
        
        if(left==nullptr&&right==nullptr)return true;
        if((left==nullptr&&right!=nullptr)||(left!=nullptr&&right==nullptr))return false;

        return ((left->val==right->val)&&(pd(left->left,right->right))&&(pd(left->right,right->left)));

    }

    bool isSymmetric(TreeNode* root) {
        if(root==nullptr)return true;
        
        return pd(root->left,root->right);

    }
};

```
