##### 题目描述
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).

Find the minimum element.

You may assume no duplicate exists in the array.

Example 1:

Input: [3,4,5,1,2] 
Output: 1
Example 2:

Input: [4,5,6,7,0,1,2]
Output: 0


##### 提交链接
https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/



##### 代码思路

参考易用写法中的二分写法


##### 代码实现

```
/*
4 5 6 1 2 3
1
1 2 3 4
*/
class Solution {
public:
    int findMin(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        if(nums.size()==1)
            return nums[0];
        int left=0,right=nums.size()-1;
        if(nums[left]<nums[right])
            return nums[left];
        while(left<right){
            int middle=left+(right-left)/2;
            if(nums[middle]>=nums[0])  //注意临界
                left=middle+1;
            else 
                right=middle;
        }
        if(left>=1 && nums[left]<=nums[left-1])
            return nums[left];
        return -1;
    }
};

```

