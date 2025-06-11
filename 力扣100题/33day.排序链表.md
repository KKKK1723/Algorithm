# 148. 排序链表  

给你链表的头结点 head ，请将其按 升序 排列并返回 排序后的链表 。  
 
 

# 示例 1：  

![image](https://github.com/user-attachments/assets/665f6714-0641-40aa-85a2-e2b67086f12a)  

输入：head = [4,2,1,3]  
输出：[1,2,3,4]  
# 示例 2：  
![image](https://github.com/user-attachments/assets/22d7c270-2754-4bf5-a156-046be0798592)  


输入：head = [-1,5,3,4,0]  
输出：[-1,0,3,4,5]  
# 示例 3：  

输入：head = []  
输出：[]  
 

# 提示：

链表中节点的数目在范围 [0, 5 * 104] 内  
-105 <= Node.val <= 105  
 
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
    ListNode* sortList(ListNode* head) {
        vector<int>p;
        ListNode* t=head;
        while(t!=nullptr)
        {
            p.emplace_back(t->val);
            t=t->next;
        }
        sort(p.begin(),p.end());

        ListNode *end=head;
        ListNode *n=end;
        for(int i=0;i<p.size();i++)
        {
            n->val=p[i];
            n=n->next;
        }
        return end;
    }
};

```
