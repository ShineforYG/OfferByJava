# 面试题30：包含min函数的栈

## 题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

## 解答

使用辅助栈记录当前最小值（动归）

~~~java
import java.util.Stack;

public class Solution {

    Stack<Integer> stack = new Stack<>();
    Stack<Integer> record = new Stack<>();

    public void push(int node) {
        if (stack.isEmpty()) {
            stack.push(node);
            record.push(node);
        } else {
            stack.push(node);
            record.push(node < record.peek() ? node : record.peek());
        }
    }

    public void pop() {
        stack.pop();
        record.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int min() {
        return record.peek();
    }
}

~~~

