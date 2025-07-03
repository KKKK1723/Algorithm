# 25. K 个一组翻转链表  

给你链表的头节点 head ，每 k 个节点一组进行翻转，请你返回修改后的链表  

k 是一个正整数，它的值小于或等于链表的长度。如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序  

你不能只是单纯的改变节点内部的值，而是需要实际进行节点交换  

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/ccc390ab-6429-43cd-8d35-8e6d63dc2abb)  


输入：head = [1,2,3,4,5], k = 2  
输出：[2,1,4,3,5]  
# 示例 2：  

![image](https://github.com/user-attachments/assets/57ecd8db-c62d-4563-8868-7f8b6f23c4e5)  


输入：head = [1,2,3,4,5], k = 3  
输出：[3,2,1,4,5]  
 

# 提示：  
链表中的节点数目为 n  
1 <= k <= n <= 5000  
0 <= Node.val <= 1000  

```
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(k==1)return head;

        vector<ListNode*>p;
        ListNode* tmp=head;
        while(tmp)
        {
            p.emplace_back(tmp);
            tmp=tmp->next;
        }

        ListNode* ans=new ListNode(0,nullptr);
        ListNode*res=ans;
        for(int i=0;i<p.size();i+=k)
        {
            if(p.size()-i<k)continue;
            for(int j=i+k-1;j<p.size(),j>=i;j--)
            {
                ans->next=p[j];

                ans=ans->next;
            }

        }

        if(p.size()%k!=0)
        {
            int num=p.size()-(p.size()%k);
            for(int i=num;i<p.size();i++)
            {
                ans->next=p[i];
                ans=ans->next;
            }
        }

        ans->next=nullptr;
        res=res->next;
        return res;
    }
};
```
