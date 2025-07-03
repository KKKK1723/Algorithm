# 21. 合并两个有序链表  

将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。   

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/ecb64679-53e5-4b2e-afb8-47d14884c6fa)  


输入：l1 = [1,2,4], l2 = [1,3,4]  
输出：[1,1,2,3,4,4]  
# 示例 2：  

输入：l1 = [], l2 = []  
输出：[]  
# 示例 3：  

输入：l1 = [], l2 = [0]  
输出：[0]  
 

# 提示：  

两个链表的节点数目范围是 [0, 50]  
-100 <= Node.val <= 100  
l1 和 l2 均按 非递减顺序 排列  

```

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1==nullptr&&list2==nullptr)return nullptr;
        if(list1==nullptr&&list2!=nullptr)return list2;
        if(list1!=nullptr&&list2==nullptr)return list1;

        bool p1=1,p2=1;
        ListNode* t1=list1;
        ListNode* t2=list2;
        ListNode* tmp;
        ListNode* head;
        if(t1->val<=t2->val)
        {
            tmp=t1;
            if(t1->next==nullptr)
            {
                p1=0;
            }
            else
            {
                t1=t1->next;
            }
        }
        else
        {
            tmp=t2;
            if(t2->next==nullptr)
            {
                p2=0;
            }
            else
            {
                t2=t2->next;
            }
        }
        head=tmp;
        while(p1&&p2)
        {
            if(t1->val<=t2->val)
            {
                tmp->next=t1;
                tmp=tmp->next;
                if(t1->next!=nullptr)
                {
                    t1=t1->next;
                }
                else
                {
                    p1=0;
                }
            }
            else
            {
                tmp->next=t2;
                tmp=tmp->next;
                if(t2->next!=nullptr)
                {
                    t2=t2->next;
                }
                else
                {
                    p2=0;
                }
            }
        }

        if(!p1&&p2)
        {
            while(p2)
            {
                tmp->next=t2;
                tmp=tmp->next;
                if(t2->next!=nullptr)
                {
                    t2=t2->next;
                }
                else
                {
                    p2=0;
                }
            }
        }
        if(p1&&!p2)
        {
            while(p1)
            {
                tmp->next=t1;
                tmp=tmp->next;
                if(t1->next!=nullptr)
                {
                    t1=t1->next;
                }
                else
                {
                    p1=0;
                }
            }
        }
        return head;
    }
};

```
