##### 题目描述
There are a total of n courses you have to take, labeled from 0 to n-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

Example 1:
```
Input: 2, [[1,0]] 
Output: true
Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0. So it is possible.
```
Example 2:
```
Input: 2, [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0, and to take course 0 you should
             also have finished course 1. So it is impossible.
```
Note:
```
The input prerequisites is a graph represented by a list of edges, not adjacency matrices. Read more about how a graph is represented.
You may assume that there are no duplicate edges in the input prerequisites.
```

##### 提交链接
https://leetcode.com/problems/course-schedule/



##### 代码思路
拓扑排序，构建一个图。
学习A课需要B课，则B指向A（学习课程的限制）

将入度为0（没有学习课程的限制）的节点依次去掉（学习了这节课）
将这个节点指出的边去掉，限制解除

最后没有入度为0的节点，则表示接下来的课都不能学了。


##### 代码实现

```
class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& pre) {
        if(numCourses<0 || pre.empty()==true)
            return true;
        vector<int> degree(numCourses,0);
        vector<vector<int>> graph(numCourses);
        for(int i=0;i<pre.size();i++){
            degree[pre[i][0]]++;
            graph[pre[i][1]].push_back(pre[i][0]);
        }
        queue<int> Q;
        vector<int> visit(numCourses,0);
        for(int i=0;i<numCourses;i++){
            if(degree[i]==0){
                Q.push(i);
                visit[i]=1;
            }    
        }
        while(Q.empty()==false){
            int tmp=Q.front();
            Q.pop();
            for(int i=0;i<graph[tmp].size();i++){
                int node=graph[tmp][i];
                degree[node]--;
                if(degree[node]==0 && visit[node]==0){
                    Q.push(node);
                    visit[node]=1;
                }
            }
        }
        for(int i=0;i<numCourses;i++){
            if(visit[i]==0)
                return false;
        }
        return true;
    }

};


```
