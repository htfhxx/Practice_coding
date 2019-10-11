##### 题目描述
Given a set of distinct integers, nums, return all possible subsets (the power set).

Note: The solution set must not contain duplicate subsets.

Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]


##### 提交链接
https://leetcode.com/problems/subsets/



##### 代码思路
子集的问题可以看作是每个字符0 or 1 ，0和1的组合就是最后的结果，即：输出的结果中有没有这个字符



##### 代码实现

```
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result;
        if(nums.empty()==true)
            return result;
        int n=nums.size();
        vector<int> path;
        dfs(nums,n,result,path,0);
        return result;
        
    }
    void dfs(vector<int> nums, int n,vector<vector<int>> &result, vector<int> path, int start){
        if(start==n){
            result.push_back(path);
            return;
        }
        dfs(nums,n,result,path,start+1);
        path.push_back(nums[start]);
        dfs(nums,n,result,path,start+1);
    }
};


```
