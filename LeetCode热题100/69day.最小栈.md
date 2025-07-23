# 最小栈





提示



设计一个支持 `push` ，`pop` ，`top` 操作，并能在常数时间内检索到最小元素的栈。

实现 `MinStack` 类:

- `MinStack()` 初始化堆栈对象。
- `void push(int val)` 将元素val推入堆栈。
- `void pop()` 删除堆栈顶部的元素。
- `int top()` 获取堆栈顶部的元素。
- `int getMin()` 获取堆栈中的最小元素。

 

**示例 1:**

```
输入：
[“MinStack”，“push”，“push”，“push”，“getMin”，“pop”，“top”，“getMin”]
[[],[-2],[0],[-3],[],[],[],[]]

输出：
[null,null,null,null,-3,null,0,-2]

解释：
MinStack minStack = new MinStack();
myStack.push(-2);
myStack.push(0);
myStack.push(-3);
minStack.getMin(); --> 返回-3.
myStack.pop()；
minStack.top(); --> 返回 0.
minStack.getMin(); --> 返回-2.
```

 

**提示：**

- `-231 <= val <= 231 - 1`
- `pop`、`top` 和 `getMin` 操作总是在 **非空栈** 上调用
- `push`, `pop`, `top`, and `getMin`最多被调用 `3 * 104` 次



```c++
class MinStack {
private:
    deque<int>dq;
    deque<int>mindq;
public:
    MinStack() {
        mindq.push_back(INT_MAX);
    }
    
    void push(int val) {
        dq.push_back(val);
        mindq.push_back(min(mindq.back(),val));
    }
    
    void pop() {
        dq.pop_back();
        mindq.pop_back();
    }
    
    int top() {
        int t=dq.back();
        return t;
    }
    
    int getMin() {
        int t=mindq.back();
        return t;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(val);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```

