arrary
```
int number[];
```

#include<string>
```
memset(a,0,sizeof(a));

```

#include<vector>
```
vector<int> v;    vector<vector<int>> v;
v.size();    v[0].size();
v.empty();  
v.push_back(x);

sort(result.begin(),result.end());  //排列
```


#include<stack>
```
stack<int> s;
s.push(value);
s.empty();
s.push(value);
s.top();
s.pop();
```
#include<queue>
```
queue<int> q;
s.push(value);
q.empty();
q.push(value);
q.front();
s.pop();
```

#include<map>
```
map<int,int> m;
m[a]=b;
```

#include<math>
```
fabs(number); //绝对值
sqt(number); //开方
```

#include<multiset>
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



