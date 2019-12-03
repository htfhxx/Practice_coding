##### 题目描述
Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

Note: Do not modify the linked list.


##### 提交链接
https://leetcode.com/problems/linked-list-cycle-ii/



##### 代码思路

1. hash表，O(n)空间，O(n)时间
2. 俩指针，O(1)空间，O(n)时间
环状链表：0-1-2-3-4-5-2（2是环状链表入口）
slow:0-1-2-3-4-5
fast:0-2-4-2-4
（4是相遇节点）
0-2：x
2-4: y
4-2：z

slow: x+y
fast: x+y+z
x+y+z =2*(x+y)
z=x+y
即：相遇的节点到入口，起点到入口距离一样

##### 代码实现

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
    ListNode *detectCycle(ListNode *head) {
        if(head==NULL)
            return NULL;
        map<ListNode*,int> m;
        while(head->next!=NULL){
            if(m.count(head)==1){
                return head;
            }
            m[head]=1;
            head=head->next;
        }
        return NULL;
    }
};


```
```
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        if(head==NULL || head->next==NULL || head->next->next==NULL)
            return NULL;
        ListNode* fast=head->next->next;
        ListNode* slow=head->next;
        while(fast!=slow){
            if(fast->next==NULL || fast->next->next==NULL)
                return NULL;
            fast=fast->next->next;
            slow=slow->next;
        }
        ListNode* meeting=fast;//meeting为相遇节点
        ListNode* result=head;    
        while(meeting!=result){
            result=result->next;
            meeting=meeting->next;
        }
        return result;
    }
};
```