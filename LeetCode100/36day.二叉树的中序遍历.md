# 94. 二叉树的中序遍历  

给定一个二叉树的根节点 root ，返回 它的 中序 遍历 。

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/a9271b72-3f04-4396-bb73-ffa727130c6f)  


输入：root = [1,null,2,3]  
输出：[1,3,2]  
# 示例 2：  

输入：root = []  
输出：[]  
# 示例 3：  

输入：root = [1]  
输出：[1]  
 

# 提示：  

树中节点数目在范围 [0, 100] 内  
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
    void dg(TreeNode* node,vector<int>& p)
        {
            if(node==nullptr)return;

            dg(node->left,p);
            p.emplace_back(node->val);
            dg(node->right,p);
        }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>p;
        dg(root,p);
        return p;
    }
};
```
 
