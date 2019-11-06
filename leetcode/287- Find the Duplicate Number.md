##### 题目描述
Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

Example 1:
```
Input: [1,3,4,2,2]
Output: 2
```
Example 2:
```
Input: [3,1,3,4,2]
Output: 3
```

Note:
```
You must not modify the array (assume the array is read only).
You must use only constant, O(1) extra space.
Your runtime complexity should be less than O(n2).
There is only one duplicate number in the array, but it could be repeated more than once.
```

##### 提交链接

https://leetcode.com/problems/find-the-duplicate-number/


##### 代码思路




##### 代码实现
hash表
```
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        map<int,int> M;
        for(int i=0;i<nums.size();i++){
            if(M[nums[i]]==1)
                return nums[i];
            if(M[nums[i]]==0)
                M[nums[i]]=1;
        }
        return -1;
    }
};
```

按位置排序
```
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        for(int i=0;i<nums.size();i++){
            while(nums[i]!=i+1){  //交换一次是不够的   每个数字最多需要swap两次
                if(nums[i]==nums[nums[i]-1])
                    return nums[i];
                else
                    swap(nums[i],nums[nums[i]-1]);
            }  
        }
        return -1;
    }
};
```