# 724_Find-Pivot-Index

[TOC]

## Description

Given an array of integers `nums`, write a method that returns the "pivot" index of this array.

We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the right of the index.

If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most pivot index.

**Example 1:**

```
Input: 
nums = [1, 7, 3, 6, 5, 6]
Output: 3
Explanation: 
The sum of the numbers to the left of index 3 (nums[3] = 6) is equal to the sum of numbers to the right of index 3.
Also, 3 is the first index where this occurs.
```

**Example 2:**

```
Input: 
nums = [1, 2, 3]
Output: -1
Explanation: 
There is no index that satisfies the conditions in the problem statement.
```

**Note:**

The length of `nums` will be in the range `[0, 10000]`.

Each element `nums[i]` will be an integer in the range `[-1000, 1000]`.

## Solution

### Java solution

```java
class Solution {
    public int pivotIndex(int[] nums) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        
        int leftSum = 0, rightSum = 0;
        for (int num : nums) {
            rightSum += num;
        }
        
        for (int i = 0; i < nums.length; ++i) {
            rightSum -= nums[i];
            if (leftSum == rightSum) {
                return i;
            }
            leftSum += nums[i];
        }
        
        return -1;
    }
}
```

Runtime: **39 ms**. Your runtime beats 72.58 % of java submissions. 

### Python solution

```python
class Solution:
    def pivotIndex(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums is None or len(nums) == 0:
            return -1
        
        left_sum, right_sum = 0, sum(nums)
        for index, num in enumerate(nums):
            right_sum -= num
            if left_sum == right_sum:
                return index
            left_sum += num
            
        return -1
```

Runtime: **72 ms**. Your runtime beats 96.94 % of python3 submissions. 