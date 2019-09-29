##### 题目描述
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]


##### 提交链接
https://leetcode.com/problems/generate-parentheses/submissions/



##### 代码思路
方法一：  O(2^n * n)
通过递归得到所有可能的结果：共2^(n)个。然后通过规则筛除不符合情况的string。

方法二：
通过递归得到所有可能的结果，在递归过程中判断能否加“)”





##### 代码实现
方法一：
```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        if(n<1)
            return vector<string>();
        vector<string> result;
        string path="";
        findNext(n,result,path,0);
        return result;
    }
    
    void findNext(int n,vector<string>& result,string path,int index){
        if(index==n*2){
            if(judge(path,n)==true)
                result.push_back(path);
            return;
        }
        findNext(n,result,path+"(",index+1);
        if(index!=0)
            findNext(n,result,path+")",index+1);
    }
    bool judge(string path,int n){
        int left=0,right=0;
        for(int i=0;i<path.size();i++){
            if(path[i]=='(')
                left++;
            else
                right++;
            if(right>left || left>n || right>n)  //left和right并不是各占一半
                return false;
        }
        return true;
    }
};


```
方法二：

```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        if(n<1)
            return vector<string>();
        vector<string> result;
        string path="";
        findNext(n,result,path,0,0);
        return result;
    }
    void findNext(int n, vector<string>& result, string path,int left, int right){
        if(left==n && right==n)
            result.push_back(path);
        if(left<n)
            findNext(n,result,path+"(",left+1,right);
        if(right<left)
            findNext(n,result,path+")",left,right+1);
        return;
    }
};
```