##### 题目描述
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

Example 1:

Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.


##### 提交链接
https://leetcode.com/problems/jump-game/



##### 代码思路
遍历过程中一步一步更新所能到达的最远距离



##### 代码实现

```
class Solution {
public:
    bool canJump(vector<int>& nums) {
        if(nums.empty()==true)
            return false;
        int max_cnt=0;
        for(int i=0;i<nums.size() && i<=max_cnt;i++){
            max_cnt=max(max_cnt,i+nums[i]);
        }
        if(max_cnt>=nums.size()-1)
            return true;
        else 
            return false;
    }
};


```
