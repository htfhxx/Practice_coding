##### 题目描述
You are given coins of different denominations and a total amount of money amount. Write a function to compute the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

Example 1:
```
Input: coins = [1, 2, 5], amount = 11
Output: 3 
Explanation: 11 = 5 + 5 + 1
```
Example 2:
```
Input: coins = [2], amount = 3
Output: -1
Note:
You may assume that you have an infinite number of each kind of coin.
```

##### 提交链接

https://leetcode.com/problems/coin-change/


##### 代码思路

coins=[1, 2, 5]   amount=11
coin=1
dp: 1 2 3 4 5 6 7 8 9 10 11
coin=2
dp: 1 1 2 2 3 3 4 4 5 5 6
coin=5
dp: 1 1 2 2 1 2 2 2 2 2 3

每次考虑只有前i个硬币，更新amount
最终的dp[amount]就是结果（注意没有组合--即dp[amount]没有更新 的情况）



##### 代码实现

```
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        if(coins.empty()==true || amount<0)  //amount=0时，return 0
            return -1;
        vector<int> dp(amount+1,amount+1);
        dp[0]=0; 
        for(int i=0;i<coins.size();i++){
            for(int j=1;j<=amount;j++){
                if(j>=coins[i])
                    dp[j]=min(dp[j],dp[j-coins[i]]+1);
            }
        }
        if(dp[amount]==amount+1)   //考虑无法组合的情况
            return -1;
        else
            return dp[amount];
    }
};

```
