##### 题目描述
Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
 
```
Example 1:

    2
   / \
  1   3

Input: [2,1,3]
Output: true
Example 2:

    5
   / \
  1   4
     / \
    3   6

Input: [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```

##### 提交链接

https://leetcode.com/problems/validate-binary-search-tree/


##### 代码思路

1. 迭代 O(n^2)，每个节点都判断一下他的左右子树的各个节点满足条件
2. 迭代，不重复的判断各个节点
3. 中序遍历，如果是BST则访问到的数字是顺序排列的


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
    bool isValidBST(TreeNode* root) {
        if(root==NULL)
            return true;
        return isValid(root,LONG_MIN,LONG_MAX);

    }
    bool isValid(TreeNode *root, long min_int ,long max_int){   //这题还要求了精度
        if(root==NULL)
            return true;
        if(root->val >= max_int || root->val<=min_int )
            return false;
        return isValid(root->left,min_int,root->val) && isValid(root->right,root->val, max_int);
    }
};


```

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
    bool isValidBST(TreeNode* root) {
        if(root==NULL)
            return true;
        long preLONG=LONG_MIN;
        return inorder(root,preLONG);
    }
    bool inorder(TreeNode* root,long& preLONG){
        if(root==NULL)
            return true;
        if(inorder(root->left,preLONG) ==false)
            return false;
        if(root->val <=preLONG)
            return false;
        preLONG=root->val;
        return inorder(root->right,preLONG);
    }
};```