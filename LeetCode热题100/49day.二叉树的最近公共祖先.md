# 236. 二叉树的最近公共祖先  

给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个节点 p、q，最近公共祖先表示为一个节点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/a78d5506-fa77-4830-ab4d-0442637c16cd)  


输入：root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1  
输出：3  
解释：节点 5 和节点 1 的最近公共祖先是节点 3 。  
# 示例 2：  
![image](https://github.com/user-attachments/assets/71ce47ad-7f78-477e-b668-c86351e20f00)  


输入：root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4  
输出：5  
解释：节点 5 和节点 4 的最近公共祖先是节点 5 。因为根据定义最近公共祖先节点可以为节点本身。  
# 示例 3：  

输入：root = [1,2], p = 1, q = 2  
输出：1  
 

## 提示：  

树中节点数目在范围 [2, 105] 内。  
-109 <= Node.val <= 109  
所有 Node.val 互不相同 。  
p != q  
p 和 q 均存在于给定的二叉树中。  

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==nullptr||root==p||root==q)return root;

        TreeNode* left=lowestCommonAncestor(root->left,p,q);
        TreeNode* right=lowestCommonAncestor(root->right,p,q);

        if(left&&right)return root;

        return left?left:right;
    }
};

```
