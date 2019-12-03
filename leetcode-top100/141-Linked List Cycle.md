##### 题目描述
Given a linked list, determine if it has a cycle in it.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.


##### 提交链接

https://leetcode.com/problems/linked-list-cycle/submissions/


##### 代码思路

1. hash表，O(n)空间，O(n)时间
2. 俩指针，O(1)空间，O(n)时间


##### 代码实现
hash表
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head==NULL)
            return false;
        map<ListNode*,int> m;
        while(head!=NULL){
            if(m.count(head)==1){
                return true;
            }
            m[head]=1;
            head=head->next;
        }
        return false;
    }
};






```

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head==NULL || head->next==NULL || head->next->next==NULL)
            return false;
        ListNode* fast=head->next->next;
        ListNode* slow=head;
        while(fast!=slow){
            if(fast->next==NULL || fast->next->next==NULL)
                return false;
            fast=fast->next->next;
            slow=slow->next;
        }
        return true;
    }
};




```