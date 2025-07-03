# 230. 二叉搜索树中第 K 小的元素

给定一个二叉搜索树的根节点 root ，和一个整数 k ，请你设计一个算法查找其中第 k 小的元素（从 1 开始计数）。  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/3ec47670-d743-4b42-bfb5-5b7962de8ed4)  


输入：root = [3,1,4,null,2], k = 1  
输出：1  
# 示例 2：  
![image](https://github.com/user-attachments/assets/744a200c-5a56-4518-a1a7-9e5e54985805)  


输入：root = [5,3,6,2,4,null,null,1], k = 3  
输出：3  
 

 

# 提示：  

树中的节点数为 n 。   
1 <= k <= n <= 104  
0 <= Node.val <= 104  

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
    int kthSmallest(TreeNode* root, int k) {
        vector<int>p;
        dg(root,p);

        sort(p.begin(),p.end());
        return p[k-1];
    }


    void dg(TreeNode* root,vector<int>&p)
    {
        if(root==nullptr)return;

        p.emplace_back(root->val);

        dg(root->left,p);
        dg(root->right,p);
    }

};

```
