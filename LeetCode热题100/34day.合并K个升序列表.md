# 23. 合并 K 个升序链表  

给你一个链表数组，每个链表都已经按升序排列。  

请你将所有链表合并到一个升序链表中，返回合并后的链表。  

 

# 示例 1：  

输入：lists = [[1,4,5],[1,3,4],[2,6]]  
输出：[1,1,2,3,4,4,5,6]  
解释：链表数组如下：  
[  
      1->4->5,  
      1->3->4,  
      2->6  
]  
将它们合并到一个有序链表中得到。  
1->1->2->3->4->4->5->6  
# 示例 2：  

输入：lists = []  
输出：[]  
# 示例 3：  

输入：lists = [[]]  
输出：[]  
 

# 提示：  

k == lists.length  
0 <= k <= 10^4  
0 <= lists[i].length <= 500  
-10^4 <= lists[i][j] <= 10^4  
lists[i] 按 升序 排列  
lists[i].length 的总和不超过 10^4  

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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
       
        vector<int>p;
        for(int i=0;i<lists.size();i++)
        {
            ListNode* tmp=lists[i];

            while(tmp!=nullptr)
            {
                p.emplace_back(tmp->val);
                tmp=tmp->next;
            }
        }

        sort(p.begin(),p.end());
        if(p.empty())return nullptr;
        ListNode* n=new ListNode(p[0]);
        ListNode* end=n;

        for(int i=1;i<p.size();i++)
        {
            n->next=new ListNode(p[i]);
            n=n->next;
        }

        return end;
    }
};

```
