##### 题目描述
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
 ```

But the following [1,2,2,null,3,null,3] is not:
```
    1
   / \
  2   2
   \   \
   3    3
```

##### 提交链接

https://leetcode.com/problems/symmetric-tree/


##### 代码思路




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
    bool isSymmetric(TreeNode* root) {
        if(root==NULL)
            return true;
        return isSym(root->left,root->right);
    }
    bool isSym(TreeNode *left,TreeNode *right){
        if(left==NULL && right==NULL)
            return true;
        if(left==NULL || right==NULL)
            return false;
        if(left->val != right->val)
            return false;
        return isSym(left->left,right->right) && isSym(left->right,right->left);
    }
};


```
