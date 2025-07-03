# 104. 二叉树的最大深度  

给定一个二叉树 root ，返回其最大深度  

二叉树的 最大深度 是指从根节点到最远叶子节点的最长路径上的节点数  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/b59dc708-ff2c-4368-b3dc-6d2475ac3615)  



 

输入：root = [3,9,20,null,null,15,7]  
输出：3  
# 示例 2：  

输入：root = [1,null,2]  
输出：2  
 

# 提示：  

树中节点的数量在 [0, 104] 区间内。  
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

    void dg(TreeNode* node,int now,int& maxx)
    {
        if(node==nullptr)return;
        maxx=max(maxx,now);

        dg(node->left,now+1,maxx);
        dg(node->right,now+1,maxx);

    }

    int maxDepth(TreeNode* root) {
        if(root==nullptr)return 0;

        int maxx=0;
        dg(root,1,maxx);

        return maxx;
    }
};
```
