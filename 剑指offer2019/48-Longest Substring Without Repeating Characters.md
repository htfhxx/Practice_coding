##### 题目描述
Given a string, find the length of the longest substring without repeating characters.


##### 提交链接
https://leetcode.com/problems/longest-substring-without-repeating-characters/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.empty()==true)
            return 0;
        int result=0;
        int currentLen=0;
        map<char,int> preIndex;
        
        for(int i=0;i<s.length();i++){
            if(preIndex.count(s[i])==0){
                currentLen++;
            }
            else{
                if(currentLen<i-preIndex[s[i]])
                    currentLen++;
                else{
                    currentLen=i-preIndex[s[i]];
                }
            }
            preIndex[s[i]]=i;
            result=max(result,currentLen);  
        }
        return result;
    }
};


```
