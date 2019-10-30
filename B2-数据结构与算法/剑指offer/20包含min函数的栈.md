
# 题目

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。


```python
# 解法一：
"""
由于要求时间复杂度为 1，因此借助一个辅助栈， 栈顶用来存储栈中的最小元素
当栈压如元素时，判断该元素 A 与辅助栈 栈顶元素 B 的大小，如果 A>B，则将 B 再次压入辅助栈，反之将 A 压入辅助栈；
出栈时，两个栈都要删除栈顶元素，这样做的目的是时刻保证两个栈中的元素是一样多的
而且，辅助栈的栈顶时刻是最小元素。
""" 
class Solution:
    def __init__(self):
        self.stack = []
        self.min_element = []
    def push(self, node):
        self.stack.append(node)
        if not self.min_element:
            self.min_element.append(node)
        else:
            if self.min_element[-1]>node:
                self.min_element.append(node)
            else:
                self.min_element.append(self.min())
    def pop(self):
        if self.stack:
            self.min_element.pop()
            return self.stack.pop()
        return None
    def top(self):
        if self.stack:
            return self.stack[-1]
        return None
    def min(self):
        return self.min_element[-1]
```


```python

```
