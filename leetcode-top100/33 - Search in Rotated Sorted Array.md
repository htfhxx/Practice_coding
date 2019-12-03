##### 题目描述
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

Example 1:

Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
Example 2:

Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1


##### 提交链接
https://leetcode.com/problems/search-in-rotated-sorted-array/



##### 代码思路
方法一：
1. 找到后一半的第一个索引mid_start
2. 判断数字在索引之前还是在索引之后确定二分范围
3. 在排序数组中找到这个数字
要考虑的样例：  
5 6 7 1 2 3  
5 1 2 3  
5 6 7 1  
1 2 3 4 5 6  
5 1    
1  

方法二：
直接二分！



##### 代码实现
方法一
```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.empty()==true)
            return -1;
        int n=nums.size();
        //找到后一半的第一个索引mid_start
        int left=0,right=n-1;
        int mid_start=0;
        if(nums[left]>nums[right]){  //middle=0的情况  1 2 3      1
            while(left<=right){
                int middle=(left+right)/2;
                if(middle>0 && nums[middle]<nums[middle-1]){  //middle=0的情况  1 2 3      1
                    mid_start=middle;
                    break;   
                }
                if(nums[middle]>=nums[0])   //考虑middle=0的情况  5 1 
                    left=middle+1;
                else 
                    right=middle-1;
            }
        }
        //判断数字在索引之前还是在索引之后
        left=0;right=n-1;
        if(mid_start!=0){
            if(target>=nums[0])
                right=mid_start-1;
            else
                left=mid_start;
        }
        //在排序数组中找到这个数字
        while(left<=right){
            int middle=(left+right)/2;
            if(target==nums[middle])
                return middle;
            if(target>nums[middle])
                left=middle+1;
            else
                right=middle-1;
        }
        return -1; 
    }
};
```

方法二
```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.empty()==true)
            return -1;
        int n=nums.size();
        int left=0,right=n-1;
        while(left<=right){
            int middle=(left+right)/2;
            if(target==nums[middle])
                return middle;
            if(nums[left]<=nums[middle]){  //查找范围内[left,middle]已排序
                if(target>=nums[left] && target<=nums[middle])  //target在排序的区间内
                    right=middle-1;
                else
                    left=middle+1;
            }
            else{  //查找范围内[middle,right]已排序
                if(target>=nums[middle] && target<=nums[right]) //target在排序的区间内
                    left=middle+1;
                else
                    right=middle-1;
            }
        }
        return -1;
    }
};
```