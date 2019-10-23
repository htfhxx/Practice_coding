##### 题目描述
Write a program to find the node at which the intersection of two singly linked lists begins.

Example 1:
```
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
Output: Reference of the node with value = 8
Input Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,0,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
```

Example 2:
```
Input: intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
Output: Reference of the node with value = 2
Input Explanation: The intersected node's value is 2 (note that this must not be 0 if the two lists intersect). From the head of A, it reads as [0,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.```
```

##### 提交链接
https://leetcode.com/problems/intersection-of-two-linked-lists/



##### 代码思路




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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(headA==NULL || headB==NULL)
            return NULL;
        ListNode* goA=headA;
        ListNode* goB=headB;
        while(goA!=NULL && goB!=NULL){
            goA=goA->next;
            goB=goB->next;
        }
        if(goB==NULL){   //让A比B短
            swap(headA,headB);
            swap(goA,goB);
        }
        ListNode *cnt=goB;
        goA=headA;
        goB=headB;
        while(cnt!=NULL){
            goB=goB->next;
            cnt=cnt->next;
        }
        while(goA!=goB){
            goA=goA->next;
            goB=goB->next;
        }
        return goA;
    }
};


```