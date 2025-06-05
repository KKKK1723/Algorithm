# 19. 删除链表的倒数第 N 个结点  

给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。

 

## 示例 1：  
![image](https://github.com/user-attachments/assets/742fb2be-71e1-4561-8f46-9561009beeb5)  


输入：head = [1,2,3,4,5], n = 2  
输出：[1,2,3,5]  
## 示例 2：  

输入：head = [1], n = 1  
输出：[]  
## 示例 3：  

输入：head = [1,2], n = 1  
输出：[1]  
 

## 提示：  

链表中结点的数目为 sz  
1 <= sz <= 30  
0 <= Node.val <= 100  
1 <= n <= sz  
 

进阶：你能尝试使用一趟扫描实现吗？  

```
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        int p=0;
        ListNode* tmp=head;
        while(1)
        {
            p++;
            if(tmp->next!=nullptr)
            {
                tmp=tmp->next;
            }
            else
            {
                break;
            }
        }

        int target=p-n+1;
        ListNode* t=new ListNode(0,head);
        ListNode* now=t;
        for(int i=1;i<target;i++)
        {
            now=now->next;
        }
            
        now->next=now->next->next;
        ListNode* res=t->next;
        delete t;
        return res;
    }
};

```
