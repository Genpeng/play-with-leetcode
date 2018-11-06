# 530_Minimum-Absolute-Difference-in-BST

[TOC]

## Description

Given a binary search tree with non-negative values, find the minimum [absolute difference](https://en.wikipedia.org/wiki/Absolute_difference) between values of any two nodes.

**Example:**

```
Input:

   1
    \
     3
    /
   2

Output:
1

Explanation:
The minimum absolute difference is 1, which is the difference between 2 and 1 (or between 2 and 3).
```

**Note:** There are at least two nodes in this BST.

## Solution


### Java solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    int minDiff = Integer.MAX_VALUE;
    TreeNode prev = null;
    
    public void inOrder(TreeNode root) {
        if (root == null) {
            return;
        }
        
        inOrder(root.left);
        
        if (prev != null) {
            minDiff = Math.min(minDiff, root.val - prev.val);
        }
        prev = root;
        
        inOrder(root.right);
    }
    
    public int getMinimumDifference(TreeNode root) {
        inOrder(root);
        return minDiff;
    }
}
```

Runtime: **8 ms**. Your runtime beats 99.91 % of java submissions.

### Python solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def getMinimumDifference(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        l = list()
        def in_order(root):
            if root:
                in_order(root.left)
                l.append(root.val)
                in_order(root.right)
        in_order(root)
        return min([b - a for a, b in zip(l, l[1:])])
```

Runtime: **72 ms**. Your runtime beats 86.68 % of python3 submissions.