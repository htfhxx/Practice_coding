##### 题目描述
Reverse a singly linked list.

Example:
```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```
Follow up:

A linked list can be reversed either iteratively or recursively. Could you implement both?


##### 提交链接
https://leetcode.com/problems/reverse-linked-list/



##### 代码思路
递归的思路
```
1->3->2->4
1->3->2<-4
1->3<-2<-4
1<-3<-2<-4
```



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
    ListNode* reverseList(ListNode* head) {
        if(head==NULL || head->next==NULL)
            return head;
        ListNode * pre=NULL;
        ListNode * curr=head;
        while(curr!=NULL){
            ListNode * tmp=curr->next;
            curr->next=pre;
            pre=curr;
            curr=tmp;
        }
        return pre;
    }
};
```

递归
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==NULL || head->next==NULL)
            return head;
        ListNode * tail=reverseList(head->next);
        head->next ->next=head;
        head->next=NULL;
        return tail;
    }
};
```
