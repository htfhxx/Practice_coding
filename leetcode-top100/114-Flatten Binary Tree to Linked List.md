##### 题目描述

Given a binary tree, flatten it to a linked list in-place.

For example, given the following tree:
```
    1
   / \
  2   5
 / \   \
3   4   6
```
The flattened tree should look like:
```
1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```
##### 提交链接

https://leetcode.com/problems/flatten-binary-tree-to-linked-list/


##### 代码思路
别忘了左树置NULL!!!!



##### 代码实现

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    void flatten(TreeNode* root) {
        if(root==NULL)
            return;
        TreeNode* tmp=root;
        while(tmp!=NULL){
            if(tmp->left==NULL){
                tmp=tmp->right;
                continue;
            }
            TreeNode *l=tmp->left;
            TreeNode *r=l;
            while(r->right!=NULL)
                r=r->right;
            r->right=tmp->right;
            tmp->right=l;
            tmp->left=NULL;   //！！！！别忘了左树置NULL
            tmp=tmp->right;
        }
    }
    
};


```
