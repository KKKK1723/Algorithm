# 437. 路径总和 III  

给定一个二叉树的根节点 root ，和一个整数 targetSum ，求该二叉树里节点值之和等于 targetSum 的 路径 的数目。  

路径 不需要从根节点开始，也不需要在叶子节点结束，但是路径方向必须是向下的（只能从父节点到子节点）。  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/73d63d7a-b399-4745-bd0a-641289c6b02b)  



输入：root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8  
输出：3  
解释：和等于 8 的路径有 3 条，如图所示。  
示例 2：  

输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22  
输出：3  
 

# 提示:  

二叉树的节点个数的范围是 [0,1000]  
-109 <= Node.val <= 109   
-1000 <= targetSum <= 1000   

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
    int pathSum(TreeNode* root, int targetSum) {
        if(root==nullptr)return 0;
        int ans=0;
        ans+=dg(root,targetSum,0);
        ans+=pathSum(root->left,targetSum);
        ans+=pathSum(root->right,targetSum);
        return ans;
    }

    int dg(TreeNode* root, int targetSum,long long sum)
    {
        if(root==nullptr)return 0;
        int p=0;

        sum+=root->val;
        if(sum==targetSum)p++;

        p+=dg(root->left,targetSum,sum);
        p+=dg(root->right,targetSum,sum);

        return p;

    }
};

```
