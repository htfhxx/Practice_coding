##### 题目描述
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

Note:

The same word in the dictionary may be reused multiple times in the segmentation.
You may assume the dictionary does not contain duplicate words.
Example 1:
```
Input: s = "leetcode", wordDict = ["leet", "code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```
Example 2:
```
Input: s = "applepenapple", wordDict = ["apple", "pen"]
Output: true
Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
             Note that you are allowed to reuse a dictionary word.
```
Example 3:
```
Input: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
Output: false
```

##### 提交链接
https://leetcode.com/problems/word-break/



##### 代码思路
1. dfs  O(n^n)
2. dp  遍历过程中，index_i在内的j个字母在字典中时，dp[i]=dp[i-j]


##### 代码实现

```
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        if(s=="" && wordDict.empty()==true)
            return true;
        if(s=="" || wordDict.empty()==true)
            return false;
        bool result=false;
        string moreString="";
        wordBreakCore(s,wordDict,moreString,result);
        return result;
    }
    void wordBreakCore(string s,vector<string> wordDict, string moreString,bool &result){
        if(result==true)
            return;
        if(moreString==s){
            result=true;
            return;
        }   
        if(moreString.size()>s.size() || moreString!=s.substr(0,moreString.size()))
            return;
        for(int i=0;i<wordDict.size();i++){
            if(wordDict[i]!=s.substr(moreString.size(),wordDict[i].size()))
                continue;
            string tmpString=moreString;
            tmpString+=wordDict[i];
            wordBreakCore(s,wordDict,tmpString,result);
        }
    }
};


```
```

class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        if(s.empty()==true && wordDict.empty()==true)
            return true;
        if(s.empty()==true || wordDict.empty()==true)
            return false;
        set<string> S(wordDict.begin(),wordDict.end());
        vector<bool> dp(s.size()+1,false);
        for(int i=0;i<s.size();i++){
            for(int j=i;j>=0;j--){
                if(S.find(s.substr(j,i-j+1))!=S.end() && (j==0 || dp[j-1]==true))
                    dp[i]=true;
            }
        }
        return dp[s.size()-1];
    }
};

```