# 747_Largest-Number-At-Least-Twice-of-Others

[TOC]

## Description

In a given integer array `nums`, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the **index** of the largest element, otherwise return -1.

**Example 1:**

```
Input: nums = [3, 6, 1, 0]
Output: 1
Explanation: 6 is the largest integer, and for every other number in the array x,
6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.
```



**Example 2:**

```
Input: nums = [1, 2, 3, 4]
Output: -1
Explanation: 4 isn't at least as big as twice the value of 3, so we return -1.
```



**Note:**

1. `nums` will have a length in the range `[1, 50]`.
2. Every `nums[i]` will be an integer in the range `[0, 99]`.

## Solution

### Java solution

```java
class Solution {
    public int dominantIndex(int[] nums) {        
        if (nums.length == 1) {
            return 0;
        }
        
        int largest = 0, secondLargest = 0, k = 0;
        for (int i=0; i<nums.length; i++) {
            if (nums[i] > largest) {
                secondLargest = largest;
                largest = nums[i];
                k = i;
            } else if (nums[i] > secondLargest) {
                secondLargest = nums[i];
            }
        }
        
        return largest >= 2*secondLargest ? k : -1;
    }
}
```

Runtime: **17 ms**

### Python solution

```python
class Solution:
    def dominantIndex(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 1:
            return 0
        
        largest, second_largest, k = 0, 0, 0
        for i, num in enumerate(nums):
            if num > largest:
                second_largest, largest, k = largest, num, i
            elif num > second_largest:
                second_largest = num
        
        if largest >= 2*second_largest:
            return k
        else:
            return -1
```

Runtime: **44 ms**