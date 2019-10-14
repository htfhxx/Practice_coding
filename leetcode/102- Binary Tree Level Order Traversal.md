##### 题目描述
Share
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree
```
[3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
```
return its level order traversal as:
```
[
  [3],
  [9,20],
  [15,7]
]
Share
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
```
return its level order traversal as:
```
[
  [3],
  [9,20],
  [15,7]
]
```

##### 提交链接
https://leetcode.com/problems/binary-tree-level-order-traversal/



##### 代码思路




##### 代码实现
写法1
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
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if(root==NULL)
            return result;
        queue<TreeNode*> Q;
        Q.push(root);
        int cnt=1;
        int next_cnt=0;
        vector<int> level;
        TreeNode *tmp_node;
        
        while(Q.empty()==false){
            tmp_node=Q.front();
            Q.pop();
            cnt--;
            level.push_back(tmp_node->val);
            if(tmp_node->left!=NULL){
                Q.push(tmp_node->left);
                next_cnt++;
            }
            if(tmp_node->right!=NULL){
                Q.push(tmp_node->right);
                next_cnt++;
            }
            if(cnt==0){
                result.push_back(level);
                level.clear();
                cnt=next_cnt;
                next_cnt=0;
            }
        }
        return result;
    }
};


```

方法2

```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if(root==NULL)
            return result;
        queue<TreeNode*> Q;
        Q.push(root);
        while(Q.empty()==false){
            int cnt=Q.size();
            vector<int> level;
            TreeNode *tmp_node;
            while(cnt--){
                tmp_node=Q.front();  Q.pop();
                level.push_back(tmp_node->val);
                if(tmp_node->left!=NULL)
                    Q.push(tmp_node->left);
                if(tmp_node->right!=NULL)
                    Q.push(tmp_node->right);
            }
            result.push_back(level);
        }
        return result;
    }
};
```