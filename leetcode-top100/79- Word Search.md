##### 题目描述
Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

Example:

board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]

Given word = "ABCCED", return true.
Given word = "SEE", return true.
Given word = "ABCB", return false.


##### 提交链接

https://leetcode.com/problems/word-search/


##### 代码思路




##### 代码实现

```

class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        if(board.empty()==true)
            return false;
        bool result=false;
        int m=board.size(), n=board[0].size();
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                dfs(board,result,i,j,word,0);
                if(result==true)
                    return true;
            }
        }
        return false;

    }
    void dfs(vector<vector<char>> &board, bool &result,int x,int y,string word,int start){
        if(result==true)   //漏掉会超时
            return;
        if(board[x][y]!=word[start])
            return;
        if(start==word.size()-1){
            result=true;
            return;
        }
        int tmp_board=board[x][y];
        board[x][y]='*';
        vector<int> dx({-1,0,0,1});
        vector<int> dy({0,1,-1,0});
        for(int i=0;i<4;i++){
            if(x+dx[i]>=0 && x+dx[i]<board.size() && y+dy[i]>=0 && y+dy[i]<board[0].size())
                dfs(board,result,x+dx[i],y+dy[i],word,start+1);
        }
        board[x][y]=tmp_board;
    }
};


```
