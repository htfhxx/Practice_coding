arrary
```
int number[];
swap(number[i],number[j]);
```

#include<string>
```
memset(a,0,sizeof(a));
str.size();  str.length();
str.begin();   str.end();
```

#include<vector>
```
vector<int> v;  
vector<int> mem(n+1,-1); //n+1个数，初始化-1

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
s.push(value);
s.empty();
s.top();
s.pop();
```

#include<queue>
```
queue<int> q;
q.push(value);
q.empty();
q.front();
s.pop();
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

#include<deque>
```
deque<int> q;
q.push_back(value);
q.empty();
q.front();
q.back();
s.pop();
```

#include<map>
```
map<int,int> m;
m.count(val)==0?
m[a]=b;
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


#include<algorithm>
```

sort(array,array+length);     //0-(length-1)数组排序
(find(result.begin(),result.end(),str) == result.end()  )  //判断vector中是否包含str

bool cmp(const int &a,const int &b) return a>b;   //没有官方封装的快
sort(array,array+length,cmp);  //0-(length-1)数组排序-降序
```



