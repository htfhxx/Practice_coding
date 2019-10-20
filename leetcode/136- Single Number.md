##### 题目描述

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example 1:

Input: [2,2,1]
Output: 1
Example 2:

Input: [4,1,2,1,2]
Output: 4

##### 提交链接
https://leetcode.com/problems/single-number/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        map<int,int> M;
        for(int i=0;i<nums.size();i++){
            if(M.count(nums[i])==0)
                M[nums[i]]=1;
            else
                M[nums[i]]++;
        }
        map<int,int>::iterator iter=M.begin();
        while(iter!=M.end()){
            if(iter->second==1)
                return iter->first;
            iter++;
        }
        return nums[0];
    }
};
```

```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        if(nums.empty()==true)
            return -1;
        for(int i=1;i<nums.size();i++){
            nums[0]^=nums[i];
        }
        return nums[0];
    }
};


```

