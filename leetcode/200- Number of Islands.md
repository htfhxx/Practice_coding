##### 题目描述
Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

Example 1:
```
Input:
11110
11010
11000
00000

Output: 1
```
Example 2:
```
Input:
11000
11000
00100
00011

Output: 3
```

##### 提交链接




##### 代码思路




##### 代码实现

```
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        if(grid.empty()==true)
            return 0;
        int m=grid.size();
        int n=grid[0].size();
        int result=0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]=='1'){
                    result++;
                    dfs(grid,i,j);
                }
            }
        }
        return result;
    }
    void dfs(vector<vector<char>> &grid,int x,int y){
        grid[x][y]=='0';
        vector<int> lr({-1,1,0,0});
        vector<int> ud({0,0,1,-1});
        for(int i=0;i<4;i++){
            int tmpX=x+lr[i],tmpY=y+ud[i];
            if(tmpX>=0 && tmpX<grid.size() && tmpY>=0 && tmpY<grid[0].size() && grid[tmpX][tmpY]=='1'){
                grid[tmpX][tmpY]='0';
                dfs(grid,tmpX,tmpY);
            }
        }
    }
};


```
