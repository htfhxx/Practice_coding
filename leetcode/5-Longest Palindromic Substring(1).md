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
        //初始化;或者说是为了dp[i][j]=dp[i+1][j-1]初始化等式后面的值
        vector<vector<int>> dp(n,vector<int>(n,0));
        for(int i=0;i<n;i++){
            dp[i][i]=1;  //每个单独的元素 回文
            if(i+1<n && s[i]==s[i+1])
                dp[i][i+1]=1;  //每两个连续的相同字符也回文
        }
        //dp的迭代
        for(int i=n-1;i>=0;i--){
            for(int j=i+2;j<n;j++){
                if(s[i]==s[j] && i+1<n && j-1>=0)
                    dp[i][j]=dp[i+1][j-1];   //取值依靠左下角的值，因此不能行列顺序遍历-> 从下到上，从左到右
            }
        }
        //找到最大的        
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

```
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.empty()==true || s.size()==1)
            return s;
        int n=s.size();
        int maxLen=0;
        string result="";
        
        //奇数个元素的回文串
        for(int i=0;i<n;i++){
            int tmpI=i,tmpJ=i; 
            if(maxLen<1){   //判断是否最终结果是一个字母或两个字母
                maxLen=1;
                result=s.substr(tmpI,tmpJ-tmpI+1);
            }
            while(tmpI-1>=0 && tmpJ+1<n && s[tmpI-1]==s[tmpJ+1]){
                tmpI-=1;
                tmpJ+=1; 
                int tmpLen=tmpJ-tmpI+1;
                if(tmpLen>maxLen){
                    maxLen=tmpLen;
                    result=s.substr(tmpI,tmpJ-tmpI+1);
                }
            }
        }
        
        //偶数个元素的回文串
        for(int i=0;i<n;i++){
            int tmpI=i,tmpJ=i+1; 
            if(s[tmpI]!=s[tmpJ])
                continue;
            if(maxLen<2){
                maxLen=2;
                result=s.substr(tmpI,tmpJ-tmpI+1);
            }
            while(tmpI-1>=0 && tmpJ+1<n && s[tmpI-1]==s[tmpJ+1]){
                tmpI-=1;
                tmpJ+=1; 
                int tmpLen=tmpJ-tmpI+1;
                if(tmpLen>maxLen){
                    maxLen=tmpLen;
                    result=s.substr(tmpI,tmpJ-tmpI+1);
                }
            }
        }
        return result;
    }
};

```
