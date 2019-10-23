##### 题目描述
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example 1:
```
Input: [3,2,3]
Output: 3
```
Example 2:
```
Input: [2,2,1,1,1,2,2]
Output: 2

```
##### 提交链接

https://leetcode.com/problems/majority-element/


##### 代码思路




##### 代码实现

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        int result=nums[0];
        int cnt=1;
        for(int i=1;i<nums.size();i++){
            if(cnt==0){
                result=nums[i];
                cnt++;
                continue;
            }
            if(nums[i]==result)
                cnt++;
            else
                cnt--;
        }
        return result;
    }
};

```
