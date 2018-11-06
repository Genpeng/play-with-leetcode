# 9_回文数（Palindrome-Number）

[TOC]

## 描述

判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**示例 1:**

```
输入: 121
输出: true
```

**示例 2:**

```
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
```

**示例 3:**

```
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```

**进阶:**

你能不将整数转为字符串来解决这个问题吗？

## 解法一：转化为字符串的比较

### 思路

将整数转化为字符串，比较逆序的字符串与原字符串是否相等即可。

### Java 实现

```java
class Solution {
    public boolean isPalindrome(int x) {
    	String reversedStr = (new StringBuilder(x + "")).reverse().toString();
    	return (x + "").equals(reversedStr);
    }
}
```

### Python 实现

```python
class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        return str(x) == str(x)[::-1]
```

### 复杂度分析

- 时间复杂度：$O(\log_{10}(n))$，其中，$n$ 表示该整数，整数的位数大约为 $\log_{10}n$
- 空间复杂度：$O(\log_{10}(n))$

## 解法二：反转数字的后半部分 ★

### 思路

对于这道题，我们可能会想到将整数直接反转后进行比较，但是反转的整数有可能大于最大的整数，从而造成整数溢出。因此，我们采用另一种做法——只反转整数的后半部分，然后判断整数的后半部分和前半部分是否相等，如果相等，则该整数就是一个回文数。当然，进行反转前需要进行一些边界判定，例如整数是否为负数（负数不可能是回文数）等。

### Java 实现

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) {
            return false;
        }
        
        int rev = 0;
        while (x > rev) {
            rev = rev * 10 + x % 10;
            x /= 10;
        }
        
        return x == rev || x == rev / 10;
    }
}
```

### Python 实现

```python
class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if (x < 0) or (x % 10 == 0 and x != 0):
            return False
        
        rev = 0
        while x > rev:
            rev = rev * 10 + x % 10
            x = x // 10
            
        if rev == x or rev // 10 == x:
            return True
        else:
            return False
```

### 复杂度分析

- 时间复杂度：$O(\log_{10}(n))$，其中 $n$ 表示输入的整数
- 空间复杂度：$O(1)$