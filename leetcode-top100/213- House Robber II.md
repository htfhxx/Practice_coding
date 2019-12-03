##### 题目描述
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

Example 1:
```
Input: [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2),
             because they are adjacent houses.
```             
Example 2:
```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```

##### 提交链接
https://leetcode.com/problems/house-robber-ii/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    int rob(vector<int>& nums) {
        if(nums.empty()==true)
            return 0;
        vector<int> dp(nums.size(),0);
        int result=0;
        
        //第一个不偷
        dp[0]=0;
        for(int i=1;i<nums.size();i++){
            if(i>=2)
                dp[i]=max(dp[i-2]+nums[i],dp[i-1]);
            else
                dp[i]=max(dp[i-1],nums[i]);
        }
        result=dp[nums.size()-1];
        
        dp.clear();
        //第一个偷
        dp[0]=nums[0];
        for(int i=1;i<nums.size()-1;i++){
            if(i>=2)
                dp[i]=max(dp[i-2]+nums[i],dp[i-1]);
            else
                dp[i]=max(dp[i-1],nums[i]);
        }
        if(nums.size()>=2)
            result=max(result, dp[nums.size()-2]); 
        else 
            result=max(result,dp[0]);
        
        return result;
        
    }
};


```
