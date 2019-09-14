##### 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。。


##### 代码实现
```
class Solution {
public:
    void push(int value) {
        data.push(value);
        if(min_data.empty()==true || min_data.top()>value)
            min_data.push(value);
        else
            min_data.push(min_data.top());
    }
    void pop() {
        data.pop();
        min_data.pop();
    }
    int top() {
        return data.top();
    }
    int min() {
        return min_data.top();
    }
private:
    stack<int> min_data;
    stack<int> data;
};

 ```     
