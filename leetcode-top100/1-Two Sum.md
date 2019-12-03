##### 题目描述
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.


##### 提交链接

https://leetcode.com/problems/two-sum/


##### 代码思路

注意原vector是未排序的。
哈希表能控制时间复杂度到O(n)。

并不需要提前遍历构建一个完整的hash表，可以边遍历边构建边判断，只要有满足条件的数字对，在最后肯定能找到的。


##### 代码实现

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        if(nums.empty()==true)
            return vector<int>();
        map<int,int> m;
        for(int i=0;i<nums.size();i++){
            if(m.count(target-nums[i])==1)
                return vector<int>({m[target-nums[i]],i});
            m[nums[i]]=i;
        }
        return vector<int>();
    }
};


```
