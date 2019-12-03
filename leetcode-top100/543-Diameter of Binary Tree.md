##### 题目描述
Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

Example:
Given a binary tree
          1
         / \
        2   3
       / \     
      4   5    
Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

Note: The length of path between two nodes is represented by the number of edges between them.

##### 提交链接
https://leetcode.com/problems/diameter-of-binary-tree/



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
    int diameterOfBinaryTree(TreeNode* root) {
        if(root==NULL)
            return 0;
        int result=0;
        getDepth(root,result);
        return result;
    }
    int getDepth(TreeNode *root, int &result){
        if(root==NULL)
            return 0;
        int left=getDepth(root->left,result);
        int right=getDepth(root->right,result);
        result=max(result,left+right);
        return max(left,right)+1;
    }
};


```
