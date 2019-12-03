##### 题目描述
Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?

Example:

Input: 3
Output: 5
Explanation:
Given n = 3, there are a total of 5 unique BST's:
```
   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```


##### 提交链接
https://leetcode.com/problems/unique-binary-search-trees/



##### 代码思路
DP
左边0~(n-1)棵树，右边(n-1)~0棵树



##### 代码实现

```
class Solution {
public:
    int numTrees(int n) {
        vector<int> result(n+2,0);
        result[0]=1;
        result[1]=1;
        for(int i=2;i<=n;i++){
            for(int j=0;j<=i-1;j++){
                result[i]+=result[j]*result[i-1-j];
            }
        }
        return result[n];
    }
};


```
