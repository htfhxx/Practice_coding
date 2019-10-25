##### 题目描述
A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null.

Return a deep copy of the list.
Input:
```
{"$id":"1","next":{"$id":"2","next":null,"random":{"$ref":"2"},"val":2},"random":{"$ref":"2"},"val":1}
```
Explanation:
```
Node 1's value is 1, both of its next and random pointer points to Node 2.
Node 2's value is 2, its next pointer points to null and its random pointer points to itself.
 ```

Note:
```
You must return the copy of the given head as a reference to the cloned list.
```
##### 提交链接
https://leetcode.com/problems/copy-list-with-random-pointer/



##### 代码思路
map存储对应的random指针
错误示例中存储原链表的current与random，本质上是原链表的指针，因此不能直接给新链表赋值
新示例中将原链表和新链表的对应节点存入map，根据原链表的random找新链表的random


##### 代码实现




错误示范（值得一看）   
```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;

    Node() {}

    Node(int _val, Node* _next, Node* _random) {
        val = _val;
        next = _next;
        random = _random;
    }
};
*/
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if(head==NULL)
            return NULL;
        map<Node*,Node*> M;
        Node* copy=new Node();
        Node* result=copy;
        Node* curr=head;
        
        while(curr!=NULL){
            M[curr]=curr->random;   //存储的实际上是原链表的指针，因此不能直接给新链表赋值
            curr=curr->next;
        }
        curr=head;
        while(curr!=NULL){
            copy->next=new Node(curr->val,curr->next,M[curr]);
            copy=copy->next;
            curr=curr->next;
        }
        return result->next;
    }
};
```
正确示例
```
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if(head==NULL)
            return NULL;
        map<Node*,Node*> M;
        Node* copy=new Node(-1,NULL,NULL);
        Node* result=copy;
        Node* curr=head;
        
        while(curr!=NULL){
            copy->next=new Node(curr->val,curr->next,NULL);
            M[curr]=copy->next;
            curr=curr->next;
            copy=copy->next;
        }
        curr=head;
        copy=result->next;
        while(curr!=NULL){
            copy->random=M[curr->random];
            copy=copy->next;
            curr=curr->next;
        }
        return result->next;
    }
};
```