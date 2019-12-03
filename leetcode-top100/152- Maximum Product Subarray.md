##### 题目描述
Given an integer array nums, find the contiguous subarray within an array (containing at least one number) which has the largest product.

Example 1:
```
Input: [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```
Example 2:
```
Input: [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```

##### 提交链接
https://leetcode.com/problems/maximum-product-subarray/



##### 代码思路




##### 代码实现

```
/*
[2,3,-2,4]
2 6 -2 4
6
*/
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        if(nums.empty()==true)
            return 0;
        int maxLast=nums[0];
        int minLast=nums[0];
        int result=nums[0];
        for(int i=1;i<nums.size();i++){
            int max_tmp=maxLast,min_tmp=minLast;
            maxLast=max(nums[i], max(nums[i] * max_tmp, nums[i] * min_tmp));
            minLast=min(nums[i], min(nums[i] * max_tmp, nums[i] * min_tmp));
            result=max(result, maxLast);
        }
        return result; 
    }
};


```
