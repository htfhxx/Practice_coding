##### 题目描述
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.


##### 提交链接
https://leetcode.com/problems/longest-palindromic-substring/



##### 代码思路
所有的子字符串+判断：O(n^3)

二维数组保存dp：  
dp[i][j]=1 代表i-j的字符串是回文串  
dp[i][j]=dp[i+1][j-1] &s[i]==s[j]


列举所有的回文串：  
i从0开始到n-1:  
i -> (i-1,i,i+1)->(i-2,i,i+2)  
if( s[i]==s[i+1])  ->   i从0开始到n-1:  
i -> (i-1,i,i+1,i+2) -> (i-2,i-1,i,i+1,i+2,i+3)







##### 代码实现


```
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.empty()==true || s.size()==1)
            return s;
        int n=s.size();
        vector<vector<int>> dp(n,vector<int>(n,0));
        for(int i=0;i<n;i++){
            dp[i][i]=1;
            if(i+1<n && s[i]==s[i+1])
                dp[i][i+1]=1;
        }
        
        for(int i=n-1;i>=0;i--){
            for(int j=i+2;j<n;j++){
                if(s[i]==s[j] && i+1<n && j-1>=0)
                    dp[i][j]=dp[i+1][j-1];   //取值依靠左下角的值，因此不能行列顺序遍历-> 
            }
        }
        /*
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                cout<<dp[i][j]<<" ";
            }
            cout<<endl;
        }
        */
                
        string result="";
        int maxLen=0;
        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                if(dp[i][j]==1 && j-i+1>maxLen){
                    maxLen=j-i+1;
                    result=s.substr(i,j-i+1);
                }
            }
        }
        return result; 
    }
};






```
