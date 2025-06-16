# 226. 翻转二叉树  

给你一棵二叉树的根节点 root ，翻转这棵二叉树，并返回其根节点  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/b3f1be77-5670-4972-b31b-b8bf94c8c31f)  



输入：root = [4,2,7,1,3,6,9]  
输出：[4,7,2,9,6,3,1]  
# 示例 2：  
![image](https://github.com/user-attachments/assets/f548bfd5-86f0-489a-917f-461afb2a27c5)  



输入：root = [2,1,3]  
输出：[2,3,1]  
# 示例 3：  

输入：root = []  
输出：[]  
 

# 提示：  

树中节点数目范围在 [0, 100] 内  
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
    TreeNode* invertTree(TreeNode* root) {
        if(root==nullptr)
        {
            return nullptr;
        }

        TreeNode* left=invertTree(root->left);
        TreeNode* right=invertTree(root->right);

        root->left=right;
        root->right=left;

        return root;
    }
};

```
