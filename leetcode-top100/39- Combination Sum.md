##### 题目描述
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:

Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
Example 2:

Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]


##### 提交链接
https://leetcode.com/problems/combination-sum/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> result;
        if(candidates.empty()==true)
            return result;
        dfs(candidates,result,vector<int>(),0, target);
        return result;
    }
    
    void dfs(vector<int> candidates, vector<vector<int>> & result, vector<int> path,int start,int target){
        if(target==0){
            result.push_back(path);
            return;
        }
        if(target<0)
            return;
        vector<int> temPath;
        for(int i=start;i<candidates.size();i++){
            temPath=path;
            temPath.push_back(candidates[i]);
            dfs(candidates,result,temPath,i,target-candidates[i]);
        }
        return;
    }
};


```
