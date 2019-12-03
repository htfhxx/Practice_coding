##### 题目描述
Given a collection of intervals, merge all overlapping intervals.

Example 1:

Input: [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
Example 2:

Input: [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
NOTE: input types have been changed on April 15, 2019. Please reset to default code definition to get new method signature.


##### 提交链接
https://leetcode.com/problems/merge-intervals/



##### 代码思路

排序+合并


##### 代码实现

```
class Solution {
public:
    static bool cmp(vector<int> &inter1,vector<int> &inter2){
        if(inter1[0]!=inter2[0])
            return inter1[0]<inter2[0];
        else
            return inter1[1]<inter2[1];
    }
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> result;
        if(intervals.empty()==true)
            return result;
        sort(intervals.begin(),intervals.end(),cmp);
        vector<int> current=intervals[0];
        for(int i=1;i<intervals.size();i++){
            if(current[1]>=intervals[i][0])
                current[1]=max(current[1],intervals[i][1]);    //注意[1,4],[2,3]的合并
            else{
                result.push_back(current);
                current=intervals[i];
            }
        }
        result.push_back(current);
        return result;
        
    }
};


```
