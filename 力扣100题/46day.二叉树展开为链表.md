# 114. 二叉树展开为链表  

给你二叉树的根结点 root ，请你将它展开为一个单链表：  

展开后的单链表应该同样使用 TreeNode ，其中 right 子指针指向链表中下一个结点，而左子指针始终为 null 。  
展开后的单链表应该与二叉树 先序遍历 顺序相同。  
 

# 示例 1：  
![image](https://github.com/user-attachments/assets/1f3a669e-ef43-471e-bad4-fbc5ead2f8c8)  


输入：root = [1,2,5,3,4,null,6]  
输出：[1,null,2,null,3,null,4,null,5,null,6]  
# 示例 2：  

输入：root = []  
输出：[]  
# 示例 3：  

输入：root = [0]  
输出：[0]  
 

## 提示：  

树中结点数在范围 [0, 2000] 内  
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
    void flatten(TreeNode* root) {
        if(root==nullptr)return;
        vector<TreeNode*>p;

        dg(root,p);

        for(int i=1;i<p.size();i++)
        {
            TreeNode* pre=p[i-1];
            TreeNode* next=p[i];

            pre->left=nullptr;
            pre->right=next;
        }
    }

    void dg(TreeNode* root, vector<TreeNode*>&p)
    {
        p.emplace_back(root);

        if(root->left)
        {
            dg(root->left,p);
        }
        if(root->right)
        {
            dg(root->right,p);
        }
    }
};
```
