# 138. 随机链表的复制  

给你一个长度为 n 的链表，每个节点包含一个额外增加的随机指针 random ，该指针可以指向链表中的任何节点或空节点。  

构造这个链表的 深拷贝。 深拷贝应该正好由 n 个 全新 节点组成，其中每个新节点的值都设为其对应的原节点的值。新节点的 next 指针和 random 指针也都应指向复制链表中的新节点，并使原链表和复制链表中的这些指针能够表示相同的链表状态。复制链表中的指针都不应指向原链表中的节点 。  

例如，如果原链表中有 X 和 Y 两个节点，其中 X.random --> Y 。那么在复制链表中对应的两个节点 x 和 y ，同样有 x.random --> y 。  

返回复制链表的头节点。  

用一个由 n 个节点组成的链表来表示输入/输出中的链表。每个节点用一个 [val, random_index] 表示：  

val：一个表示 Node.val 的整数。  
random_index：随机指针指向的节点索引（范围从 0 到 n-1）；如果不指向任何节点，则为  null 。  
你的代码 只 接受原链表的头节点 head 作为传入参数。  

 

# 示例 1：  

![image](https://github.com/user-attachments/assets/25dc55c6-818a-499f-b467-6ad4a27dcf24)  


输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]  
输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]  
# 示例 2：  

![image](https://github.com/user-attachments/assets/3bc31dd9-36d0-444e-bf0a-e1c3c341390c)  


输入：head = [[1,1],[2,1]]  
输出：[[1,1],[2,1]]  
# 示例 3：  
![image](https://github.com/user-attachments/assets/77f828fe-b374-425e-8203-e2149ec419f7)  



输入：head = [[3,null],[3,0],[3,null]]  
输出：[[3,null],[3,0],[3,null]]  
 

# 提示：  

0 <= n <= 1000  
-104 <= Node.val <= 104  
Node.random 为 null 或指向链表中的节点。  


```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/

class Solution {
public:
    Node* copyRandomList(Node* head) {
        //临时哨兵节点
        Node tmp{0, head, nullptr};
        //新链表的哨兵节点
        Node new_tmp{0, nullptr, nullptr};
        //用于遍历的游标指针
        Node* p = &tmp;
        Node* new_p = &new_tmp;

        while(p->next != nullptr){
            //复制一个对应位置节点
            new_p->next = new Node{p->next->val, nullptr, nullptr};
            //原链表节点扩容保存额外信息
            p->next->random = new Node{0, new_p->next, p->next->random};
            //转移至下一节点
            new_p = new_p->next;
            p = p->next;
        }
        //处理random
        p = &tmp;
        new_p = &new_tmp;
        while(p->next != nullptr){
            Node* extra_info = p->next->random;
            new_p->next->random = extra_info->random == nullptr ? nullptr : extra_info->random->random->next;
            //转移至下一节点
            new_p = new_p->next;
            p = p->next;
        }
        //原链表恢复原样，删除扩容信息
        p = &tmp;
        while(p->next != nullptr){
            Node* extra_info = p->next->random;
            p->next->random = extra_info->random;
            delete extra_info;
            //转移至下一节点
            p = p->next;
        }
        return new_tmp.next;
    }
};



```
 
