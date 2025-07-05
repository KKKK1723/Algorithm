# 124. 二叉树中的最大路径和  

二叉树中的 路径 被定义为一条节点序列，序列中每对相邻节点之间都存在一条边。同一个节点在一条路径序列中 至多出现一次 。该路径 至少包含一个 节点，且不一定经过根节点。  

路径和 是路径中各节点值的总和。  

给你一个二叉树的根节点 root ，返回其 最大路径和 。  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/a4aa3f0e-bcfe-47fb-a209-5b68794f4aea)  


输入：root = [1,2,3]  
输出：6  
解释：最优路径是 2 -> 1 -> 3 ，路径和为 2 + 1 + 3 = 6  
# 示例 2：    
![image](https://github.com/user-attachments/assets/1c2e9b4d-c731-42cd-b4ce-01c36039da52)  


输入：root = [-10,9,20,null,null,15,7]  
输出：42  
解释：最优路径是 15 -> 20 -> 7 ，路径和为 15 + 20 + 7 = 42  
 

## 提示：  

树中节点数目范围是 [1, 3 * 104]  
-1000 <= Node.val <= 1000  

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
private:
        int maxsum=INT_MIN;
public:
    int maxPathSum(TreeNode* root) {
        dfs(root);
        return maxsum;
    }


    int  dfs(TreeNode*root)
    {
        if(root==nullptr)return 0;

        int left=max(dfs(root->left),0);
        int right=max(dfs(root->right),0);

        int tmp=(root->val+left+right);
        maxsum=max(maxsum,tmp);//以此节点为根的最大值

        return root->val+max(left,right);//选一边
    }
};

```
