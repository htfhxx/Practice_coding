##### 题目描述
Given an array of strings, group anagrams together.

Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
Note:

All inputs will be in lowercase.
The order of your output does not matter.


##### 提交链接
https://leetcode.com/problems/group-anagrams/submissions/



##### 代码思路




##### 代码实现

```
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> result;
        if(strs.empty()==true)
            return result;
        unordered_map<string,vector<string>> hash;
        for(int i=0;i<strs.size();i++){
            string tem_string=strs[i];
            sort(tem_string.begin(),tem_string.end());
            hash[tem_string].push_back(strs[i]);
        }
        unordered_map<string,vector<string>>::iterator  iter=hash.begin();
        while(iter!=hash.end()){
            result.push_back(iter->second);
            iter++;
        }
        return result;
    }
};


```
