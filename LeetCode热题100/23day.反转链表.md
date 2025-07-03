# 206. 反转链表  
   
## 给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。  
 
 
# 示例 1：  
![image](https://github.com/user-attachments/assets/6bffbf64-a0af-48d7-afb1-86f240aba32d)  


输入：head = [1,2,3,4,5]  
输出：[5,4,3,2,1]  

# 示例 2：  
![image](https://github.com/user-attachments/assets/347623f0-7bf8-4c08-bf79-fd0b54f270f8)  


输入：head = [1,2]  
输出：[2,1]  

# 示例 3：  

输入：head = []  
输出：[]  
 

提示：  

链表中节点的数目范围是 [0, 5000]  
-5000 <= Node.val <= 5000  



```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *nexttmp=head;
        ListNode *nowtmp=nullptr;
        while(nexttmp!=nullptr)
        {
            ListNode* p=nexttmp->next;
            nexttmp->next=nowtmp;

            nowtmp=nexttmp;
            nexttmp=p;

        }

        return nowtmp;
       
    }
};
```
