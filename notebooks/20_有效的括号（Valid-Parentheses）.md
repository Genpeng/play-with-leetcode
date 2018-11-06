# 20_有效的括号（Valid-Parentheses）

[TOC]

## 描述

给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'` 的字符串，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

**示例 1:**

```
输入: "()"
输出: true
```

**示例 2:**

```
输入: "()[]{}"
输出: true
```

**示例 3:**

```
输入: "(]"
输出: false
```

**示例 4:**

```
输入: "([)]"
输出: false
```

**示例 5:**

```
输入: "{[]}"
输出: true
```

## 解法

### 思路

遍历字符串的每个字符，如果字符是左半边的括号（即 `(`、`[` 或者`{`），将字符压入栈；如果字符是右半边括号（即 `)`、`]` 或者 `}`），此时首先判断堆栈是否为空，如果栈为空，则该字符无法找到匹配的括号，返回 `false`，如果栈不为空，则弹出栈顶元素并与之比较，如果两个字符不相同，同样返回 `false`。最后，遍历完整个字符串后，还需要判断堆栈是否为空，如果为空，则是有效的括号，反之则为无效的括号。

### Java 实现

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (int i=0; i<s.length(); i++) {
            char c = s.charAt(i);

            if (c == '(' || c == '[' || c == '{') {
                stack.push(c);
            } else {
                if (stack.empty()) {
                    return false;
                }

                char topChar = stack.pop();
                if (c == ')' && topChar != '(') {
                    return false;
                }
                if (c == ']' && topChar != '[') {
                    return false;
                }
                if (c == '}' && topChar != '{') {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
```

**改进版：**

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(') {
                stack.push(')');
            } else if (c == '[') {
                stack.push(']');
            } else if (c == '{') {
                stack.push('}');
            } else if (stack.isEmpty() || c != stack.pop()) {
                return false;
            }
        }
        return stack.isEmpty();
    }
}
```

### Python 实现

**实现1：**

```python
class Solution:
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = list()
        for si in s:
            if si == '(':
                stack.append(')')
            elif si == '[':
                stack.append(']')
            elif si == '{':
                stack.append('}')
            elif len(stack) == 0 or si != stack.pop():
                return False
        return len(stack) == 0
```

**实现 2（借助字典）：**

```python
class Solution:
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = list()
        dict = {'(': ')', '[': ']', '{': '}'}
        for c in s:
            if c in dict.keys():
                stack.append(dict[c])
            elif c in dict.values():
                if len(stack) == 0 or c != stack.pop():
                    return False
            else:
                False
        return len(stack) == 0
```

### 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示字符串的长度
- 空间复杂度：$O(n)$，最坏的情况下，堆栈需要存放字符串的所有字符

