##### 题目描述
Given preorder and inorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree.

For example, given
```
preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
```
Return the following binary tree:
```
    3
   / \
  9  20
    /  \
   15   7
```

##### 提交链接
https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/



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
/*
preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
*/
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {      
        if(preorder.empty()==true || inorder.empty()==true || preorder.size()!=inorder.size() )
            return NULL;
        TreeNode* result=buildTreeCore(preorder,inorder, 0,preorder.size()-1,0, preorder.size()-1);
        return result;
    }
    TreeNode * buildTreeCore(vector<int> preorder, vector<int> inorder,int l1, int l2, int r1, int r2){
        if(l1>l2 || r1>r2)
            return NULL;
        int root_val=preorder[l1];
        TreeNode *root=new TreeNode(root_val);
        int root_index;
        for(int i=r1;i<=r2;i++){
            if(root_val==inorder[i])
                root_index=i;
        }
        root->left=buildTreeCore(preorder,inorder,l1+1,l1+root_index-r1,r1,root_index-1);
        root->right=buildTreeCore(preorder,inorder,l1+root_index-r1+1,l2,root_index+1,r2);
        return root;
    }
};








```
