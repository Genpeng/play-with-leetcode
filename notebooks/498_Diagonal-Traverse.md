# 498_Diagonal-Traverse

[TOC]

## Description

Given a matrix of M x N elements (M rows, N columns), return all elements of the matrix in diagonal order as shown in the below image.

**Example:**

```markdown
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output:  [1,2,4,7,5,3,6,8,9]
```

**Explanation:**
![explanation](../figs/diagonal_traverse.png)

**Note:**

1. The total number of elements of the given matrix will not exceed 10,000.

## Solution

### Java solution

```java
class Solution {
    public int[] findDiagonalOrder(int[][] matrix) {
        if (matrix == null || matrix.length == 0) {
            return new int[0];
        }

        int m = matrix.length, n = matrix[0].length;

        int[] res = new int[m * n];
        int row = 0, col = 0, d = 1;
        for (int i = 0; i < m*n; i++) {
            res[i] = matrix[row][col];

            row -= d;
            col += d;

            // lower border
            if (row >= m) {
                row -= 1;
                col += 2;
                d = -d;
            }

            // right border
            if (col >= n) {
                col -= 1;
                row += 2;
                d = -d;
            }

            // upper border
            if (row < 0) {
                row = 0;
                d = -d;
            }

            // left border
            if (col < 0) {
                col = 0;
                d = -d;
            }
        }

        return res;
    }
}
```

Runtime: **7 ms**. Your runtime beats 97.45 % of java submissions.

### Python solution 1

```python
class Solution:
    def findDiagonalOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if matrix == []:
            return []
        m, n = len(matrix), len(matrix[0])
        coordinates = [(i, j) for i in range(m) for j in range(n)]
        coordinates.sort(key=lambda x: sum(x) * max(m, n) - x[sum(x) % 2])
        return [matrix[x][y] for x, y in coordinates]
```

Runtime: **164 ms**. Your runtime beats 37.74 % of python3 submissions.

### Python solution 2

```python
class Solution:
    def findDiagonalOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        entries = [(i + j, (j, i)[(i ^ j) & 1], val)
                   for i, row in enumerate(matrix)
                   for j, val in enumerate(row)]
        return [e[2] for e in sorted(entries)]
```

Runtime: **136 ms**. Your runtime beats 77.36 % of python3 submissions.

### Python solution 3

```python
class Solution:
    def findDiagonalOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        m, n = len(matrix), len(matrix and matrix[0])
        return [matrix[i][d-i]
                for d in range(m+n-1)
                for i in range(max(0, d-n+1), min(d+1, m))[::d%2*2-1]]
```

Runtime: **148 ms**. Your runtime beats 59.43 % of python3 submissions.