# 7_反转整数（Reverse-Integer）

[TOC]

## 描述

给定一个 32 位有符号整数，将整数中的数字进行反转。

**示例 1:**

```
输入: 123
输出: 321
```

 **示例 2:**

```
输入: -123
输出: -321
```

**示例 3:**

```
输入: 120
输出: 21
```

**注意:**

假设我们的环境只能存储 32 位有符号整数，其数值范围是 $[-2^{31},\,2^{31} - 1]$。根据这个假设，如果反转后的整数溢出，则返回 0。

## 方法一

### 思路

~~输入的整数除以 10 得到商和余数，接着将返回的结果（初始值为 0）乘以 10 加上得到的余数作为新的结果，最后判断结果是否溢出（大于 32 位整数的最大值或者小于 32 位整数的最小值），将商作为新的整数重复上述过程，如果商为 0 则程序结束。~~

可以将求整数逆序数的过程想象成两个栈之间的弹出和压入操作。一个整数的每一位数存放在栈的每一格中，最高位存放在栈底，最低位存放在栈顶。将栈 A 的栈顶弹出，压入栈 B 的栈底，重复上述过程直到栈 A 为空，此时就完成了求整数逆序数的功能。实际中，弹出和压入操作并不需要借助真正的栈，可以通过求余（数学运算）实现。

其实，Python 语言的整数类型的取值范围并不存在限制，因此更不存在所谓的溢出。

### Java 实现

```java
class Solution {
    public int reverse(int x) {
        long result = 0;
        while (x != 0) {
            result = result * 10 + x % 10;
            x = x / 10;
            if (result < Integer.MIN_VALUE || result > Integer.MAX_VALUE) {
                return 0;
            }
        }
        return (int) result;
    }
}
// Runtime: 23 ms
// Your runtime beats 77.34 % of java submissions.
```

**复杂度分析：**

- 时间复杂度：$O(log(n))$
- 空间复杂度：$O(1)$

### 类似的 Java 实现

```java

class Solution {
	public int reverse(int x) {
        int ret = 0;
        while (x != 0) {
            int pop = x % 10;
            if (ret > Integer.MAX_VALUE / 10 || (ret == Integer.MAX_VALUE / 10 && pop > 7)) {
                return 0;
            }
            if (ret < Integer.MIN_VALUE / 10 || (ret == Integer.MIN_VALUE / 10 && pop < -8)) {
                return 0;
            }
            ret = ret * 10 + pop;
            x = x / 10;
        }
        return ret;
	}
}
// Runtime: 21 ms
// Your runtime beats 99.21 % of java submissions.
```

复杂度分析同上。

### Python 实现

```python
class Solution:
    def reverse(self, x):
        """
        Arguments:
        ----------
        x : int, the value range is [-2147483648, 2147483647]

        Return:
        -------
        ret : int, the reverse order number
        """
        rev, a = 0, abs(x)
        while a:
            rev = rev * 10 + a % 10
            a = a // 10
        if x > 0 and rev < 2**31:
            return rev
        elif x < 0 and rev <= 2**31:
            return -rev
        else:
            return 0
        
# Runtime: 56 ms
# Your runtime beats 85.51 % of python3 submissions.
```

复杂度分析同上。

## 方法二：转化为求字符串的倒序

### Java 实现

```Java
class Solution {
    public int reverse(int x) {
        if (x == 0) {
            return 0;
        }

        boolean isPos = x > 0;

        StringBuilder sb = new StringBuilder();
        char[] chars = String.valueOf(x).toCharArray();
        for (int i = chars.length - 1; i >= 0; --i) {
            if (chars[i] == '0' && sb.length() == 0) {
                continue;
            }
            if (chars[i] == '-') {
                continue;
            }
            sb.append(chars[i]);
        }

        String xStr = null;
        if (isPos) {
            xStr = sb.toString();
        } else {
            xStr = "-" + sb.toString();
        }

        int rev;
        try {
            rev = Integer.valueOf(xStr);
        } catch (Exception e) {
            return 0;
        }
        return rev;
    }
}
```

**复杂度分析：**

- 时间复杂度：$O(log(n))$
- 空间复杂度：$O(1)$

### Python 实现

```python
class Solution:
    def reverse(self, x):
        """
        Arguments:
        ----------
        x : int, the value range is [-2147483648, 2147483647]

        Return:
        -------
        ret : int, the reverse order number
        """
        sign = [1, -1][x < 0]
        rev = sign * int(str(abs(x))[::-1])
        return rev if -2**31 <= rev <= 2**31 - 1 else 0

# Runtime: 76 ms
# Your runtime beats 42.26 % of python3 submissions.
```

复杂度分析同上。