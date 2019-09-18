##### 题目描述
A message containing letters from A-Z is being encoded to numbers using the following mapping:  
'A' -> 1  
'B' -> 2  
...  
'Z' -> 26  
Given a non-empty string containing only digits, determine the total number of ways to decode it.  

和剑指offer不太一样
##### 提交链接
https://leetcode.com/problems/decode-ways/

##### 代码思路
vector<int> len; 代表以s[i]为结尾的字符串有几种翻译方法.  
len[i+1]=len[i] + len[i-2]   (如果i-2与i-1连成的数字可以翻译成字母)

##### 代码实现

```
class Solution {
public:
    int numDecodings(string s) {
        if(s.empty()==true || s[0]=='0') //注意0开头是不能翻译的
            return 0;
        vector<int> len(s.size(),0);
        len[0]=1;
        for(int i=1;i<s.length();i++){
            int digit1=s[i-1]-'0',digit2=s[i]-'0';
            int digit=10*digit1+digit2;
            if(s[i]!='0')
                len[i]=len[i-1];
            if(digit<=26 && digit>=10)
                if(i>=2)
                    len[i]+=len[i-2];   
                else 
                    len[i]+=1;
        }
        return len[s.length()-1]; 
    }
};
```
