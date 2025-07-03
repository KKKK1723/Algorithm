# 199. 二叉树的右视图

给定一个二叉树的 根节点 root，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。  

 

# 示例 1：  

输入：root = [1,2,3,null,5,null,4]  

输出：[1,3,4]  

解释：  
![image](https://github.com/user-attachments/assets/3ef7e924-de72-4550-bf57-09b540d45abb)  



# 示例 2：  

输入：root = [1,2,3,4,null,null,null,5]  

输出：[1,3,4,5]  

解释：  
![image](https://github.com/user-attachments/assets/50a556dc-f877-4dcd-80d3-ec0664fd4885)  



# 示例 3：  

输入：root = [1,null,3]  

输出：[1,3]  

# 示例 4：  

输入：root = []  

输出：[]  

 

## 提示:  

二叉树的节点个数的范围是 [0,100]  
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
    vector<int> rightSideView(TreeNode* root) {
        vector<int>e;
        queue<TreeNode*>q;
        if(root==nullptr)return e;

        q.push(root);

        while(!q.empty())
        {
            int n=q.size();
            for(int i=n;i>=1;i--)
            {
                TreeNode* now=q.front();
                q.pop();

                if(i==1)
                {
                    e.emplace_back(now->val);
                }

                if(now->left)
                {
                    q.push(now->left);
                }
                if(now->right)
                {
                    q.push(now->right);
                }
            }
        }

        return e;
    }
};

```
