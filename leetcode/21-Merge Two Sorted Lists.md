##### 题目描述
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4


##### 提交链接
https://leetcode.com/problems/merge-two-sorted-lists/



##### 代码思路

除了遍历外，还可以递归


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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        //if(l1==NULL && l2==NULL)
        //    return NULL;
        ListNode *newNode=new ListNode(0);
        ListNode *result=newNode;
        while(l1!=NULL && l2!=NULL){
            if(l1->val<l2->val){
                newNode->next=l1;
                l1=l1->next;
            }
            else{
                newNode->next=l2;
                l2=l2->next;
            }
            newNode=newNode->next;
        }
        if(l1!=NULL)
            newNode->next=l1;
        else
            newNode->next=l2;
        return result->next;
        
    }
};


```
递归写法

```

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1==NULL && l2==NULL)
            return NULL;
        else if(l1==NULL && l2!=NULL)
            return l2;
        else if(l1!=NULL && l2==NULL)
            return l1;
        else{
            if(l1->val<l2->val){
                l1->next=mergeTwoLists(l1->next,l2);
                return l1;
            }
            else{
                l2->next=mergeTwoLists(l1,l2->next);
                return l2;
            }
        }
    }
};
```