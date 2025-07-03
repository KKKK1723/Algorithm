# 543. 二叉树的直径  

给你一棵二叉树的根节点，返回该树的 直径 。  

二叉树的 直径 是指树中任意两个节点之间最长路径的 长度 。这条路径可能经过也可能不经过根节点 root 。  

两节点之间路径的 长度 由它们之间边数表示。  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/6a9574d0-dc3b-4da7-bf50-6aad2f3a226e)  


输入：root = [1,2,3,4,5]  
输出：3  
解释：3 ，取路径 [4,2,1,3] 或 [5,2,1,3] 的长度。  
# 示例 2：  

输入：root = [1,2]  
输出：1  
 

# 提示：

树中节点数目在范围 [1, 104] 内  
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
    int ans;
    int depth(TreeNode* root)
    {
        if(root==NULL)
        {
            return 0;
        }

        int left=depth(root->left);
        int right=depth(root->right);

        ans=max(ans,left+right+1);

        return max(left,right)+1;
    }

    int diameterOfBinaryTree(TreeNode* root) {
        ans=1;
        depth(root);
        return ans-1;
    }
};


```
