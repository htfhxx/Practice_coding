##### 题目描述
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Example:

Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
##### 提交链接
https://leetcode.com/problems/letter-combinations-of-a-phone-number/



##### 代码思路
逐个遍历字符串的字符，拼接，由于结果较多，采用递归，时间复杂度是O(4^n)


##### 代码实现

```
class Solution {
    vector<string> number2letter{"abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
public:
    vector<string> letterCombinations(string digits) {
        if(digits.empty()==true)
            return vector<string>();
        vector<string> result;
        string path="";
        findNext(digits, result,path,0);
        return result;
        
    }
    void findNext(string digits,vector<string>& result,string path,int index){
        if(index==digits.size()){ //注意边界条件，不是digits.size()-1
            result.push_back(path);
            return;
        }
        for(int i=0;i<number2letter[digits[index]-'2'].size();i++){
            string tmpPath=path+number2letter[digits[index]-'2'][i];
            findNext(digits,result,tmpPath,index+1);
        }
        return;
    }
};


```
