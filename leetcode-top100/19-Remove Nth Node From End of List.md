##### 题目描述
Given a linked list, remove the n-th node from the end of list and return its head.

Example:

Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
Note:

Given n will always be valid.

Follow up:

Could you do this in one pass?


##### 提交链接
https://leetcode.com/problems/remove-nth-node-from-end-of-list/



##### 代码思路

输入的是
1 2 3 4 5
去除倒数第：2个

first:1->2  
first:3 4 5
second:1 2 3



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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(head==NULL || n<1)
            return NULL;
        ListNode* newNode=new ListNode(0); //要考虑去除的是头结点
        newNode->next=head;
        ListNode* first=newNode;
        ListNode* second=newNode;
        for(int i=0;i<n;i++){
            if(first->next!=NULL)  //考虑n比size大
                first=first->next;
            else
                return NULL;  //本质上是exception
        }
        while(first->next!=NULL){
            first=first->next;
            second=second->next;
        }
        if(second->next!=NULL && second->next->next!=NULL)  //考虑去除节点是最后一个
            second->next=second->next->next;
        else
            second->next=NULL;
        return newNode->next;
        
    }
};


```
