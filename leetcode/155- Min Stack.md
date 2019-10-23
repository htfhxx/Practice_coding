##### 题目描述
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.
 

Example:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

##### 提交链接

https://leetcode.com/problems/min-stack/


##### 代码思路




##### 代码实现

```
class MinStack {
public:
    /** initialize your data structure here. */
    stack<int> nums;
    stack<int> min_nums;
    MinStack() {
    }
    void push(int x) {
        nums.push(x);
        if(min_nums.empty()==true)
            min_nums.push(x);
        else
            min_nums.push( min(min_nums.top(),x));
    }
    void pop() {
        nums.pop();
        min_nums.pop();
    }
    int top() {
        return nums.top();
    }
    int getMin() {
        return min_nums.top(); 
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */


```
