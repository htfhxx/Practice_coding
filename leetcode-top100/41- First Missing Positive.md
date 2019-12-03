##### 题目描述
Given an unsorted integer array, find the smallest missing positive integer.

Example 1:

Input: [1,2,0]
Output: 3
Example 2:

Input: [3,4,-1,1]
Output: 2
Example 3:

Input: [7,8,9,11,12]
Output: 1
Note:

Your algorithm should run in O(n) time and uses constant extra space.


##### 提交链接

https://leetcode.com/problems/first-missing-positive/



##### 代码思路
逐个将数字与其对应的索引上的数字调换位置，知道该位置上的数字与索引对应，或者是没有对应的索引(负数或者超过范围)。

重新遍历一下，没有出现在对应索引上的数字即为结果。


##### 代码实现

```
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        if(nums.empty()==true)
            return 1;
        for(int i=0;i<nums.size();i++){
            while(nums[i]>0 && nums[i]<nums.size() && nums[i]!=nums[nums[i]-1]){    // nums[i]!=i+1不对，反例：[1,1]  还要考虑nums[i]-1]超范围
                swap(nums[i],nums[nums[i]-1]);
            }
        }
        for(int i=0;i<nums.size();i++){
            if(nums[i]!=i+1)
                return i+1;
        }
        return nums.size()+1;
    }
};


```
