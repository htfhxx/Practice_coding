##### 题目描述
Share
Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

Example:

Input: 
```
1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

Output: 4
```

##### 提交链接
https://leetcode.com/problems/maximal-square/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if(matrix.empty()==true)
            return 0;
        int m=matrix.size();
        int n=matrix[0].size();
        vector<vector<int>> dp(m, vector<int>(n,0));
        for(int j=0;j<n;j++)
            dp[0][j]=matrix[0][j]-'0';
        for(int i=0;i<m;i++)
            dp[i][0]=matrix[i][0]-'0';
        int result=1;
        if(dp[0][0]==0 &&  (m<=1 || dp[1][0]==0) && (n<=1 || dp[0][1]==0))     //必不可少
            result=0; 
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                if(matrix[i][j]=='0')
                    dp[i][j]=0;
                else 
                    dp[i][j]=min(min(dp[i-1][j],dp[i][j-1]),dp[i-1][j-1])+1;
                    result=max(result,dp[i][j]);
            }
        }
        return result * result ;
    }
};


```
