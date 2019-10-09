arrary
```
int number[];
int dp[n][n]={0};
swap(number[i],number[j]);
```

#include<algorithm>
```
sort(array,array+length);     //0-(length-1)数组排序
bool cmp(const int &a,const int &b) return a>b;   //没有官方封装的快
sort(array,array+length,cmp);  //0-(length-1)数组排序-降序
```

#include<string>
```
str.size();  str.length();
memset(a,0,sizeof(a));
string subS=str.substr(begin_index,length_index);
```

#include<vector>
```
vector<int> v;  
vector<int> v(n+1,-1); //n+1个数，初始化-1
vector<vector<int>> v(n,vector<int>(n,0));
vector<int>({1,2,3,4});//直接加入元素
vector<int>(); //返回一个空的容器

vector<vector<int>> v;
v.size();    v[0].size();
v.empty();  
v.push_back(x);
v.clear(); //清空元素，但不回收空间

swap(v[i],v[j]);
sort(result.begin(),result.end());  //排列
```


#include<stack>
```
stack<int> s;
s.empty();
s.push(value);
s.top();
s.pop();
```

#include<queue>
```
queue<int> q;
q.empty();
q.push(value);
q.front();
s.pop();
```


#include<map>
```
map<int,int> m;
m[key]=val;
m.count(val)==0?
m.erase(key);   m.erase(iter);

map<int, int>::iterator iter=m.begin();
while(iter != m.end()) {
    cout << iter->first << " : " << iter->second << endl;
    iter++;
}
//map中的元素按照key顺序排列，在对顺序有要求的问题中使用map，查找速度上慢于哈希实现的unordered_map

```
#include<list>
```
list<int> l;
l.begin();  l.end();
l.size();
list<int>::iterator current=l.begin();
l.erase(current);
l.push_back(val);
```

#include<deque>  //双向队列
```
deque<int> q;
q.push_back(value);
q.empty();
q.front();
q.back();
s.pop();
```



#include<math>
```
fabs(number); //绝对值
sqt(number); //开方
```

#include<multiset>  //自动排序的set
```
multiset<int, greater<int> > leastNums;  //从大到小排序

leastNums.end();  //最后一个元素之后的迭代器，不是最后一个元素
leastNums.insert(val);
leastNums.erase(least.begin());
result=vector<int> (leastNumbers.begin(),leastNumbers.end());

```






