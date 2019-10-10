##### 题目描述
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example:

Input:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
Output: 7
Explanation: Because the path 1→3→1→1→1 minimizes the sum.


##### 提交链接
https://leetcode.com/problems/minimum-path-sum/



##### 代码思路




##### 代码实现

```
/*
F(m,n)=min(F(m-1,n),F(m,n-1))+grid[m][n]
*/
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        if(grid.empty()==true)
            return 0;
        int m=grid.size(),n=grid[0].size();
        vector<int> dp(n,0);
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(i==0 && j==0)
                    dp[j]=grid[i][j];
                else if(i==0 && j!=0)
                    dp[j]=dp[j-1]+grid[i][j];  //别忘了加上新加的节点
                else if(i!=0 && j==0)
                    dp[j]=dp[j]+grid[i][j];
                else    
                    dp[j]=min(dp[j],dp[j-1])+grid[i][j];
            }
        }
        return dp[n-1];
    }
};


```
