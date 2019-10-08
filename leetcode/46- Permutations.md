##### 题目描述
Given a collection of distinct integers, return all possible permutations.

Example:

Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]


##### 提交链接
https://leetcode.com/problems/permutations/



##### 代码思路

dfs列出来所有的排列

开一个vector，用来保存是否访问过这个索引。


##### 代码实现
```
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> result;
        if(nums.empty()==true)
            return result;
        vector<int> visit(nums.size(),0);  //对应索引的数字是否使用
        vector<int> path(nums.size(),-1);
        dfs(nums,result,visit,path,0);
        return result;
    }
    void dfs(vector<int> nums, vector<vector<int>> & result,vector<int> visit, vector<int> path,int cnt){  //path里的数字数量
        if(cnt==nums.size())
            result.push_back(path);
        for(int i=0;i<nums.size();i++){
            if(visit[i]==1)
                continue;
            visit[i]=1;
            path[cnt]=nums[i];
            dfs(nums, result,visit,path,cnt+1);
            visit[i]=0;
        }
    }
};


```
