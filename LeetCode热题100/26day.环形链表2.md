# 142. 环形链表 II  

给定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

不允许修改 链表。

 

# 示例 1：  
![image](https://github.com/user-attachments/assets/deb971b0-cc8f-4fb0-a60c-6919b71210b8)  



输入：head = [3,2,0,-4], pos = 1  
输出：返回索引为 1 的链表节点    
解释：链表中有一个环，其尾部连接到第二个节点。  
# 示例 2：  
![image](https://github.com/user-attachments/assets/eceb7a13-e2cf-4f60-9759-0e8c9b748538)  



输入：head = [1,2], pos = 0  
输出：返回索引为 0 的链表节点  
解释：链表中有一个环，其尾部连接到第一个节点。  
# 示例 3：  
![image](https://github.com/user-attachments/assets/3935a7fd-084f-41e5-a60d-f55a6ac1780d)  
 


输入：head = [1], pos = -1  
输出：返回 null  
解释：链表中没有环。  
 

# 提示：  

链表中节点的数目范围在范围 [0, 104] 内  
-105 <= Node.val <= 105  
pos 的值为 -1 或者链表中的一个有效索引  

```
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        set<ListNode*>st;
        ListNode* tmp=head;
        if(head==nullptr||head->next==nullptr)return nullptr;

        bool k=0;
        while(tmp->next!=nullptr)
        {
            if(st.count(tmp))
            {
                k=1;
                break;
            }
            st.insert(tmp);
            tmp=tmp->next;
        }

        if(!k)return nullptr;

        ListNode* p=head;
        int t=0;
        while(1)
        {
            if(p==tmp)
            {
                return p;
            }
            t++;
            p=p->next;
        }
    }
};
```
