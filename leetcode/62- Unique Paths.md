##### 题目描述
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?


Above is a 7 x 3 grid. How many possible unique paths are there?

Note: m and n will be at most 100.

Example 1:

Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Right -> Down
2. Right -> Down -> Right
3. Down -> Right -> Right
Example 2:

Input: m = 7, n = 3
Output: 28


##### 提交链接
https://leetcode.com/problems/unique-paths/



##### 代码思路
1. 最开始的想法-dfs(超时)

2. F(m,n)=F(m-1,n)+F(m,n-1)
3. 继续精简代码（空间复杂度）
4. 从网格左上角到网格右下角一共要走m+n-2步，在这些步数中，一共会向下走m-1步，向右走n-1步，因此就是经典的组合问题，结果就是Cn−1m+n−2Cm+n−2n−1。这样空间复杂度为O(1)O(1)，时间复杂度为O(n)O(n)。


##### 代码实现
最开始的想法-dfs(超时)
```
class Solution {
public:
    int uniquePaths(int m, int n) {
        int result=0;
        if(m<1 || n<1)
            return result;
        dfs(result,m,n,0,0);
        return result; 
    }
    void dfs(int &result,int m,int n,int i,int j){
        if(i==m-1 && j==n-1){
            result++;
            return;
        }
        if(j+1<n)
            dfs(result,m,n,i,j+1);
        if(i+1<m)
            dfs(result,m,n,i+1,j);
    }
};


```


DP的方法
```
class Solution {
public:
    int uniquePaths(int m, int n) {
        if(m<1 || n<1)
            return 0;
        vector<vector<int>> dp(m,vector<int>(n,0));
        for(int i=0;i<m;i++)
            dp[i][0]=1;
        for(int i=0;i<n;i++)
            dp[0][i]=1;
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j]=dp[i-1][j]+dp[i][j-1];
            }
        }
        return dp[m-1][n-1]; 
    }
};
```

精简dp
```
class Solution {
public:
    int uniquePaths(int m, int n) {
        if(m<1 || n<1)
            return 0;
        vector<int> dp(n,0);
        for(int i=0;i<n;i++)
            dp[i]=1;
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[j]=dp[j-1]+dp[j];
            }
        }
        return dp[n-1]; 
    }
};
```

组合的方法
```
/*
C_(m+n-2) ^(n-1)= (m-1+1 * m+1 *m+2...*m+n-2) /(1 * 2 * .. n-1)
*/
class Solution {
public:
    int uniquePaths(int m, int n) {
        if(m<1 || n<1)
            return 0;
        int total=m+n-2;
        long long int result=1;
        if(m<n)   //C的上标尽可能小
            swap(m,n);
        for(int i=m;i<=total;i++)
            result*=i;
        for(int i=1;i<=n-1;i++)
            result/=i;
        return result;
    }
};
```