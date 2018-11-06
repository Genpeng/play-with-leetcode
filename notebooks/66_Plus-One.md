# 66_Plus-One

[TOC]

## Description

Given a **non-empty** array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

**Example 1:**

```
Input: [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

**Example 2:**

```
Input: [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

## Solution

### Java solution

```java
class Solution {
    public int[] plusOne(int[] digits) {
        int n = digits.length;
        for (int i=n-1; i>=0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        
        int[] newNum = new int[n+1];
        newNum[0] = 1;
        return newNum;
    }
}
```

Runtime: **0 ms**

### Python solution 1

```python
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        i = len(digits) - 1
        while digits[i] == 9 and i>=0:
            digits[i] = 0
            i -= 1
        
        if i < 0:
            return [1] + digits
        else:
            digits[i] += 1
            return digits
```

Runtime: **44 ms**

### Python solution 2

```python
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        num = 0
        for i in range(len(digits)):
            num += digits[i] * pow(10, len(digits)-1-i)
        return [int(n) for n in str(num+1)]
```

Runtime: **40 ms**

### Python solution 3

```python
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        return [int(n) for n in str(int(''.join(map(str, digits))) + 1)]
```

Runtime: **40 ms**

