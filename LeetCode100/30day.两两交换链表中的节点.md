# 24. 两两交换链表中的节点  

给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/f72efb3e-f2e3-4bf3-b62c-9aea009798ff)  


输入：head = [1,2,3,4]  
输出：[2,1,4,3]  
# 示例 2：  

输入：head = []  
输出：[]  
# 示例 3：  

输入：head = [1]  
输出：[1]  
 

# 提示：  
 
链表中节点的数目在范围 [0, 100] 内  
0 <= Node.val <= 100  


```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) 
    {
        vector<ListNode*>p;
        ListNode* tmp=head;

        while(tmp)
        {
            p.emplace_back(tmp);
            tmp=tmp->next;
        }

        ListNode *ans=new ListNode(0,nullptr);
        ListNode* res=ans;
        for(int i=0,j=1;i<p.size()-1,j<p.size();i+=2,j+=2)
        {
            ans->next=p[j];
            ans=ans->next;

            ans->next=p[i];
            ans=ans->next;
        }
    
        if(p.size()%2!=0)
        {
            ans->next=p[p.size()-1];
            ans=ans->next;
        }
        ans->next=nullptr;


        res=res->next;
        return res;


    }
};

```
