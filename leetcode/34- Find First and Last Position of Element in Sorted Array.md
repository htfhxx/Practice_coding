##### 题目描述
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]


##### 提交链接
https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/



##### 代码思路
二分查找 找到第一个index和最后一个index（注意判断条件）



##### 代码实现

```
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> result({-1,-1});
        if(nums.empty()==true)
            return result;
        int left=0,right=nums.size()-1;
        int index1=-1,index2=-1;;
        while(left<=right){
            int middle=(left+right)/2;
            if(nums[middle]==target && (middle==0 || nums[middle]>nums[middle-1])  ){
                index1=middle;
                break;
            }
            if(target<=nums[middle])  //考虑nums[middle]==target 但不是第一个
                right=middle-1;
            else
                left=middle+1;
        }
        if(index1==-1)
            return result;
        left=index1,right=nums.size()-1;
        while(left<=right){
            int middle=(left+right)/2;
            if(nums[middle]==target && (middle==nums.size()-1 || nums[middle]<nums[middle+1])  ){
                index2=middle;
                break;
            }
            if(target<nums[middle])  //考虑nums[middle]==target 但不是最后一个
                right=middle-1;
            else
                left=middle+1;
        }
        result.clear();  
        result.push_back(index1);  
        result.push_back(index2);
        return result;
    }
};


```
