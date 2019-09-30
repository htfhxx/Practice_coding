##### 题目描述
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:

Input: "()"
Output: true
Example 2:

Input: "()[]{}"
Output: true
Example 3:

Input: "(]"
Output: false
Example 4:

Input: "([)]"
Output: false
Example 5:

Input: "{[]}"
Output: true



##### 提交链接

https://leetcode.com/problems/valid-parentheses/


##### 代码思路




##### 代码实现

```
class Solution {
public:
    bool isValid(string s) {
        if(s.empty()==true)
            return true;
        stack<char> charStack;
        for(int i=0;i<s.size();i++){
            if(s[i]=='(' || s[i]=='[' || s[i]=='{')
                charStack.push(s[i]);
            else if(s[i]==')'){
                if(charStack.empty()==true || charStack.top()!='(')
                    return false;
                charStack.pop();
            }
            else if(s[i]==']'){
                if(charStack.empty()==true || charStack.top()!='[')
                    return false;
                charStack.pop();
            }
            else if(s[i]=='}'){
                if(charStack.empty()==true || charStack.top()!='{')
                    return false;
                charStack.pop();
            }
        }
        if(charStack.empty()==true)
            return true;
        else
            return false;
        
    }
};


```
