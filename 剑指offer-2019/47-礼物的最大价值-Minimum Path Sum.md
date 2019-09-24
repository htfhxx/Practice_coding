##### 题目描述
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.


##### 提交链接
https://leetcode.com/problems/minimum-path-sum/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        if(grid.empty()==true)
            return 0;
        vector<int> len(grid[0].size(),0);
        for(int i=0;i<grid.size();i++){
            for(int j=0;j<grid[0].size();j++){
                if(i==0 && j==0){
                    len[j]=grid[i][j];
                }
                else if(i==0 && j>0){
                    len[j]=len[j-1]+grid[i][j];
                }
                else if(i>0 && j==0){
                    len[j]=len[j]+grid[i][j];
                }
                else{
                    len[j]=min(len[j-1],len[j])+grid[i][j];
                }
            }
        }
        return len[grid[0].size()-1];
        
    }
};


```
