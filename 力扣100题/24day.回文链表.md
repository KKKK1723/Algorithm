# 234. 回文链表  

## 给你一个单链表的头节点 head ，请你判断该链表是否为回文链表。如果是，返回 true；否则，返回 false 。  

 

## 示例 1：  
![image](https://github.com/user-attachments/assets/43065800-3ee2-4515-a962-def1cd9e7da4)  


输入：head = [1,2,2,1]  
输出：true  

# 示例 2：  
![image](https://github.com/user-attachments/assets/b6e8dd8b-7111-4577-84f3-4125edd52f5e)  


输入：head = [1,2]  
输出：false  
 

提示：  

链表中节点数目在范围[1, 105] 内  
0 <= Node.val <= 9  



```
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        if(head->next==nullptr||head==nullptr)return true;

        vector<int>p;
        ListNode *now=head;
        while(now)
        {
            p.emplace_back(now->val);
            now=now->next;
        }

        int left=0;
        int right=p.size()-1;
        while(left<=right)
        {
            if(p[left]!=p[right])return false;

            left++;
            right--;
        }
        return true;
    }
};

```
