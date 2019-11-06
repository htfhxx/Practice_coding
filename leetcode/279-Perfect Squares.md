##### 题目描述
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

Example 1:
```
Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
```
Example 2:
```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

##### 提交链接


https://leetcode.com/problems/perfect-squares/

##### 代码思路
超时的dfs做法，深搜到每个路径然后取最小，时间复杂度是O((logn)^n) (应该没错)

换dp，以n=10为例，最大的可能值分别有：
1. 一个9、一个1
2. 两个4、一个1
3. 一个4、六个1
4. 零个4、十个1  

即判断离10最近的平方项们：9、4、1哪个最值得加
dp[10]=min( dp[10-1\*1]+1, dp[10-2\*2]+1, dp[10-3\*3]+1 )



##### 代码实现
DP
```
class Solution {
public:
    int numSquares(int n) {
        if(n<0)
            return 0;
        int len= sqrt(n);
        vector<int> result(n+1,n);  //全部都是1的情况才会count=1
        result[0]=0;
        for(int i=1;i<=n;i++){
            for(int j=1;j*j<=i;j++){
                result[i]=min(result[i-j*j]+1,result[i]);
            }
        }
        return result[n];
    }
};
```

超时的dfs做法
```
class Solution {
public:
    int numSquares(int n) {
        if(n<0)
            return 0;
        int len= sqrt(n);
        int result=n;
        dfs(n, len, result, 0, n);
        return result;
    }
    
    void dfs(int n, int len, int &result, int cnt, int rest){
        if(rest<0)
            return;
        if(rest==0){
            result=min(result,cnt);
            return;
        }
        for(int i=len;i>=1;i--){
            dfs(n, len, result, cnt+1, rest-i*i);
        }
    }
};
```
