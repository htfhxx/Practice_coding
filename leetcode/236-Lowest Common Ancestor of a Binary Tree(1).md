##### 题目描述
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

Given the following binary tree:  root = [3,5,1,6,2,0,8,null,null,7,4]

Example 1:
```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
```
Example 2:
```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```
##### 提交链接
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/



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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL || p==NULL || q==NULL)
            return NULL;
        if(root==p || root==q)
            return root;
        TreeNode * left=lowestCommonAncestor(root->left,p,q);
        TreeNode * right=lowestCommonAncestor(root->right,p,q);
        if(left && right)
            return root;
        else if(left && !right)
            return left;
        else if(!left && right)
            return right;
        else
            return NULL;
    }
};

```
超内存的实现（如果有一个超级长的树，所有节点都只有左子树）
```
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL || p==NULL || q==NULL)
            return NULL;
        vector<TreeNode*> path1;
        vector<TreeNode*> path2;
        vector<TreeNode*> result1;
        vector<TreeNode*> result2;
        findPath(root,p,result1,path1,false);
        findPath(root,q,result2,path2,false);
        //要考虑根节点总是第一个
        for(int i=min(result1.size(),result2.size())-1;i>=0;i--){
            if(result1[i]==result2[i])
                return result1[i];
        }
        return NULL;
    }
    
    void findPath(TreeNode* root,TreeNode* p,vector<TreeNode*> &result,vector<TreeNode*> path, bool find){
        if(root==NULL)  //勿漏
            return;
        if(find==true)
            return;
        if(root==p){
            path.push_back(root);
            result=path;
            find=true;
        }
        else{
            path.push_back(root);
            findPath(root->left,p,result,path,find);  //要想起来指针之前是否为NULL
            findPath(root->right,p,result,path,find);
        }
    }
};


```


