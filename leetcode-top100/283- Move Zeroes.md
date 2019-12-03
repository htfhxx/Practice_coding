##### 题目描述
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.
```

##### 提交链接
https://leetcode.com/problems/move-zeroes/



##### 代码思路
[0,1,0,3,12]
维护两个指针，一个i用来赋值，一个j寻找下一个非0的数字



##### 代码实现

```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        if(nums.empty()==true)
            return;
        int i=0;
        for(int j=0;j<nums.size();j++){
            if(nums[j]!=0)
                 nums[i++]=nums[j];
        }
        for(;i<nums.size();i++)
            nums[i]=0;
    }
};


/* 随手的略菜的实现
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        if(nums.empty()==true)
            return;
        int n=nums.size();
        int cnt=0;
        for(int i=0;i<n;i++)
            if(nums[i]==0)
                cnt++;
        int bias=0;
        for(int i=0;i<=n-1-cnt;i++){
            nums[i]=nums[i+bias];
            while(nums[i]==0){
                bias++;
                nums[i]=nums[i+bias];
            } 
        }
        for(int i=n-cnt;i<n;i++)
            nums[i]=0;
    }
};
*/


```
