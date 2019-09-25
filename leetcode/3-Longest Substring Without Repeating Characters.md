##### 题目描述



##### 提交链接




##### 代码思路
1.从第1,2,3..n-1的位置开始，每次取最长，判断是否包含重复字符，时间复杂度O(n^3)
2. 用set构造一个滑动窗口，i和j作为滑动窗口起点和终点的索引并在每一次比较后更新i\j，并保存j-i+1的最大值。时间复杂度O(n)
3. 滑动窗口改进：维护一个map，保存字符及其索引，这样只需要遍历窗口右边的index



##### 代码实现
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.empty()==true)
            return 0;
        map<char,int> m;
        int i=0;
        int result=1;  //非空肯定有1个字符
        for(int j=0;j<s.size();j++){
            if(m.count(s[j])==1){
                i=max(m[s[j]]+1,i);//出现过的重复字符的后一位，与i比较是为了遍历到的重复字符其实是在最开始重复，i不能往前走
            }
            m[s[j]]=j;
            result=max(result,j-i+1);
        }
        return result;
    }
};
```

map改为数组，减少时间开销。
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.empty()==true)
            return 0;
        vector<int> m(256,-1);
        int i=0;
        int result=1;  //非空肯定有1个字符
        for(int j=0;j<s.size();j++){
            if(m[s[j]]!=-1){
                i=max(m[s[j]]+1,i);//出现过的重复字符的后一位，与i比较是为了遍历到的重复字符其实是在最开始重复，i不能往前走
            }
            m[s[j]]=j;
            result=max(result,j-i+1);
        }
        return result;
    }
};

```