##### 题目描述
Given an unsorted array of integers, find the length of longest increasing subsequence.

Example:
```
Input: [10,9,2,5,3,7,101,18]
Output: 4 
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```
Note:
```
There may be more than one LIS combination, it is only necessary for you to return the length.
Your algorithm should run in O(n2) complexity.
```
Follow up: Could you improve it to O(n log n) time complexity?


##### 提交链接

https://leetcode.com/problems/longest-increasing-subsequence/


##### 代码思路
O(n*n)的dp，就是遍历每个字符nums[i]，查找这个字符之前的字符nums[j],当nums[i]>nums[j]，根据dp[j]选择是否更新dp[i]。

O(n*logn)的dp，就是遍历每个字符nums[i]，维护一个到目前为止的最长递增子串，并持续更新————替换掉比nums[i]大的第一个dp[index]。
例如，nums: [3,5,6,2,5,4,19,5,6,7,12]
dp的变化过程：
```
3 
3 5 
3 5 6 
2 5 6 
2 5 6 
2 4 6 
2 4 6 19 
2 4 5 19 
2 4 5 6 
2 4 5 6 7 
2 4 5 6 7 12 
```
替换而不是添加的操作，目的是确保： 后序出现更长递增子串时，前面已经被更新。
3 5 6  -> 2 5 6 -> 2 4 6 -> 2 4 5
这样结果长度不会改变，然后-> 2 4 5 6

##### 代码实现
dp O(n*n)
```
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if(nums.empty()==true)
            return 0;
        int n=nums.size();
        vector<int> dp(n,1);
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                if(nums[i]>nums[j])
                    dp[i]=max(dp[i],dp[j]+1);
            }
        }
        int result=1;
        for(int i=0;i<n;i++)    //不是简单的返回dp[n-1]，因为最长的连续子串的末尾不一定是最后一个字符
            result=max(result,dp[i]);
        return result;
    }
};


```
dp  O(n*logn)
```
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if(nums.empty()==true)
            return 0;
        vector<int> dp;
        int N = nums.size();
        dp.push_back(nums[0]);
        for (int i = 0 ; i < N ;i ++){
            //int index = lower_bound(dp.begin(),dp.end(), nums[i])-dp.begin();
            
            int left=0,right=dp.size(); //左闭右开
            while(left<right){
                int middle=(left+right)/2;
                if(dp[middle]<nums[i])
                    left=middle+1;
                else
                    right=middle;
            }
            int index=left;
            
            //cout << "index:  "<<index<<endl;
            if (index == dp.size()){
                dp.push_back(nums[i]);
            }
            else
                dp[index] = nums[i];
            //for(int i=0;i<dp.size();i++)
            //    cout<<dp[i]<<" ";
            //cout<<endl;
        }
        return dp.size();
    }
};
```