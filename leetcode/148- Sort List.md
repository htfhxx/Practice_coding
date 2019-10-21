##### 题目描述
Sort a linked list in O(n log n) time using constant space complexity.

Example 1:
```
Input: 4->2->1->3
Output: 1->2->3->4
```
Example 2:
```
Input: -1->5->3->4->0
Output: -1->0->3->4->5
```

##### 提交链接
https://leetcode.com/problems/sort-list/



##### 代码思路
归并



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
    ListNode* sortList(ListNode* head) {
        if(head==NULL)
            return NULL;
        if(head->next==NULL)
            return head;
        ListNode* fast=head;
        ListNode* slow=head;
        while(fast->next!=NULL && fast->next->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
        }
        fast=slow->next;
        slow->next=NULL;
        slow=head;
        slow=sortList(slow);
        fast=sortList(fast);
        return mergeListNode(slow,fast);
    }
    ListNode* mergeListNode(ListNode* slow,ListNode *fast){
        if(slow==NULL)
            return fast;
        if(fast==NULL)
            return slow;
        if(slow->val<fast->val){
            slow->next=mergeListNode(slow->next,fast);
            return slow;
        }
        else{
            fast->next=mergeListNode(slow,fast->next);
            return fast;
        }

    }
};


```
