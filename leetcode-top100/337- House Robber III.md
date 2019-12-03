##### 题目描述
The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.

Example 1:
```
Input: [3,2,3,null,3,null,1]

     3
    / \
   2   3
    \   \ 
     3   1

Output: 7 
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```
Example 2:
```
Input: [3,4,5,1,3,null,1]

     3
    / \
   4   5
  / \   \ 
 1   3   1

Output: 9
Explanation: Maximum amount of money the thief can rob = 4 + 5 = 9.
```

##### 提交链接
https://leetcode.com/problems/house-robber-iii/



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
    int rob(TreeNode* root) {
        if(root==NULL)
            return 0;
        map<TreeNode*, int> M;
        dfs(root,M);
        return M[root];
    }
    void dfs(TreeNode* root,map<TreeNode*, int>& M){
        if(root==NULL)
            return;
        int val=root->val;
        if(root->left){
            dfs(root->left->left,M);
            dfs(root->left->right,M);
            val=val + M[root->left->left] + M[root->left->right];
        }
        if(root->right){
            dfs(root->right->left,M);
            dfs(root->right->right,M);
            val=val + M[root->right->left] + M[root->right->right];
        }
        if(!M[root->left])   //减少不必要的时间消耗
            dfs(root->left, M);
        if(!M[root->right])
            dfs(root->right, M);
        M[root]=max(val,M[root->left]+M[root->right]);
    }
};


```
