# 105. 从前序与中序遍历序列构造二叉树  

给定两个整数数组 preorder 和 inorder ，其中 preorder 是二叉树的先序遍历， inorder 是同一棵树的中序遍历，请构造二叉树并返回其根节点。  

 

# 示例 1:  
![image](https://github.com/user-attachments/assets/565cdaa6-d781-4ef8-93de-34ac4553132c)  


输入: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]  
输出: [3,9,20,null,null,15,7]  
# 示例 2:  

输入: preorder = [-1], inorder = [-1]  
输出: [-1]  
 

## 提示:  

1 <= preorder.length <= 3000  
inorder.length == preorder.length  
-3000 <= preorder[i], inorder[i] <= 3000  
preorder 和 inorder 均 无重复 元素  
inorder 均出现在 preorder  
preorder 保证 为二叉树的前序遍历序列  
inorder 保证 为二叉树的中序遍历序列   


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
    unordered_map<int,int> index;
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        int n=inorder.size();
        for(int i=0;i<n;i++)
        {
            index[inorder[i]]=i;
        }

        return tn(preorder,inorder,0,n-1,0,n-1);
    }

    TreeNode* tn(vector<int>& preorder, vector<int>& inorder,int xleft,int xright,int zleft,int zright)
    {
        //出口
        if(xleft>xright)return nullptr;


        //此时的根节点
        TreeNode * root=new TreeNode(preorder[xleft]);

        //左侧数量
        int sumleft=index[preorder[xleft]]-zleft;
        //右侧数量
        int sumright=zright-index[preorder[xleft]];

        root->left=tn(preorder,inorder,xleft+1,xleft+sumleft,zleft,index[preorder[xleft]]-1);

        root->right=tn(preorder,inorder,xleft+sumleft+1,xright,index[preorder[xleft]]+1,zright);



        return root;
    }

};
```
