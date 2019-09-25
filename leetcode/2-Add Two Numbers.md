##### 题目描述
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.


##### 提交链接

https://leetcode.com/problems/add-two-numbers/


##### 代码思路

关于维护一个新的链表，在初始化的时候可以新建一个节点，然后直接在这个节点之后加入新的节点，最后返回的是第一个节点的后一个节点。


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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        if(l1==NULL || l2==NULL)
            return NULL;
        ListNode *p1=l1,*p2=l2;
        ListNode *result=new ListNode(0);
        ListNode *current=result;
        int carry=0;
        while(p1!=NULL || p2!=NULL){
            int num1= (p1!=NULL) ? p1->val :0;
            int num2= (p2!=NULL) ? p2->val :0;
            int sum=(num1+num2+carry)%10;
            carry=(num1+num2+carry)/10;
            current->next=new ListNode(sum);
            current=current->next;
            if(p1) p1=p1->next;
            if(p2) p2=p2->next;
        }
        if(carry)
            current->next=new ListNode(carry);
        return result->next;
        
    }
};


```
