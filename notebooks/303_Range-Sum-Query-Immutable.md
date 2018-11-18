> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

给定一个整数数组  *nums*，求出数组从索引 *i* 到 *j*  (*i* ≤ *j*) 范围内元素的总和，包含 *i,  j* 两点。

**示例：**

```
给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```

**说明:**

1. 你可以假设数组不可变。
2. 会多次调用 *sumRange* 方法。

# 解法一：穷举法（超时）

## 思路

每次调用 `sumRange(i, j)` 方法时，遍历数组中索引从 `i` 到 `j` 的元素，对它们进行求和。

## Java 实现

```java
class NumArray {
    private int[] data;

    public NumArray(int[] nums) {
        data = nums;
    }

    public int sumRange(int i, int j) {
        int sum = 0;
        for (int k = i; k <= j; ++k) {
            sum += data[k];
        }
        return sum;
    }
}
```

## Python 实现

```python

```

## 复杂度分析

- 时间复杂度：
- 空间复杂度：

