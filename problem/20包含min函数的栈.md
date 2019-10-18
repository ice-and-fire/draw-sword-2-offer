# 题目描述
[定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。](https://www.nowcoder.com/practice/4c776177d2c04c2494f2555c9fcc1e49?tpId=13&tqId=11173&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

# 解题思路
使用另一个辅助栈来存储最小值，主栈入栈时，检查辅栈的栈顶元素，小于等于辅栈的栈顶元素即同时也入辅栈。</br>
即辅栈存储了主栈出现的最小值，栈顶元素总是所有元素中的最小值。

# 代码实现
```cpp
class Solution {
    stack<int> stack1, min_stack;
public:
    void push(int value) {
        stack1.push(value);
        if (min_stack.empty() || value <= min_stack.top()) {
            min_stack.push(value);
        }
    }
    void pop() {
        if (stack1.top() == min_stack.top()) {
            min_stack.pop();
        }
        if (!stack1.empty())
            stack1.pop();
    }
    int top() {
        return stack1.top();
    }
    int min() {
        return min_stack.top();
    }
};
```
