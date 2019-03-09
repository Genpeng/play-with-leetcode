> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

给定一个字符串，请你找出其中不含有重复字符的 **最长子串** 的长度。

**示例 1:**

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2:**

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

# 解法一：暴力枚举法（Time Limit Exceeded）

## 思路

这种方法采用的思路是：列举出字符串中所有的子串，然后判断字串是否不包含重复字符，如果是，则将该子串的长度与当前保存的最长长度（用一个变量存储）进行比较，保留二者的大者。遍历完所有的子串后，将可以得到不包含重复元素的最长子串的长度。

## Java 实现

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int ans = 0;
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j <= n; ++j) {
                if (allUnique(s, i, j)) {
                    ans = Math.max(ans, j - i);
                }
            }
        }
        return ans;
    }

    private boolean allUnique(String s, int start, int end) {
        Set<Character> set = new HashSet<>();
        for (int i = start; i < end; ++i) {
            Character ch = s.charAt(i);
            if (set.contains(ch)) {
                return false;
            }
            set.add(ch);
        }
        return true;
    }
}
```

## Python 实现

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        def is_unique(s, start, end):
            ch_has_seen = set()
            for c in s[start:end]:
                if c in ch_has_seen:
                    return False
                else:
                    ch_has_seen.add(c)
            return True

        ans = 0
        for i in range(len(s)):
            for j in range(1, len(s) + 1):
                if is_unique(s, i, j):
                    ans = max(j - i, ans)
        return ans
```

## 复杂度分析

- 时间复杂度：$O(n^3)$，其中，$n$ 表示字符串的长度。对于每个字符串中的每个子串，需要 $j -i$ 次操作才能判断该子串是否不包含重复字符（遍历子串的每个字符），因此，总的操作次数为 $\sum_{i=0}^{n-1}\sum_{j=i+1}^{n} (j-i) = \sum_{i=0}^{n} \frac{(n - i -+1)(n - i)}{2}$，即时间复杂度为 $O(n^3)$ 
- 空间复杂度：$O(\min(n, \,m))$，其中，$n$ 表示字符串的长度，$m$ 表示字符集中字符的数目。方法中需要占用 $O(k)$ 大小的空间用于存储看过的字符集（$k$ 表示集合的大小），而 $k$ 的上界主要取决于字符串的长度 $n$ 和字符集中字符的数目 $m$

# 解法二：滑动窗口（双指针）

## 思路

解法二借助于一个大小可变的滑动窗口。当窗口中不存在重复字符时，窗口的右边界向右滑动（增加窗口中的字符数），如果窗口中存在重复字符，则将窗口的左边界向右滑动，减少窗口中的字符数。并且，每次增加新的字符时，都与当前最长子串的长度进行比较，保留二者的大者。当窗口的右边界抵达字符串的末尾时，遍历结束，返回保存的最长子串的长度。滑动窗口可以采用集合进行表示。

## Java 实现

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int ans = 0, l = 0, r = 0;
        Set<Character> set = new HashSet<>();
        while (l < n && r < n) {
            if (!set.contains(s.charAt(r))) {
                set.add(s.charAt(r++));
                ans = Math.max(r - l, ans);
            } else {
                set.remove(s.charAt(l++));
            }
        }
        return ans;
    }
}
```

## Python 实现

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        l, r, max_len = 0, 0, 0
        substring = set()
        while l < len(s) and r < len(s):
            if s[r] in substring:
                substring.remove(s[l])
                l += 1
            else:
                substring.add(s[r])
                r += 1
                max_len = max(r - l, max_len)
        return max_len
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示字符串的长度。最坏情况下（例如：字符串 `bbbbbb`），需要 $2n$ 次操作
- 空间复杂度：$O(\min(n, \,m))$，其中，$n$ 表示字符串的长度，$m$ 表示字符集中字符的数目

# 解法三：滑动窗口（优化版）

## 思路

假设当窗口的右边界向右滑动添加一个字符后，窗口中的子串存在重复的字符，按照解法二的方法，则会将窗口的左边界向右滑动一个字符直到窗口中不存在重复字符为止。这样的做法其实是不高效的，比如重复的字符位于子串的右半部分，那么至少需要迭代 $len(\text{substring}) / 2$ 次才能使得窗口包含的子串不包含重复的字符。

因此，为了更加高效地完成这个过程，我们可以借助一个 `map` ——保存字符最近一次的地址。当子串因为添加一个字符发生重复时，从 `map` 中拿出新增字符最近一次的地址（索引），并将窗口的左边界直接移动到该地址的下一个字符，则此时窗口中的子串不再包含重复的字符。

## Java 实现

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int ans = 0;
        Map<Character, Integer> map = new HashMap<>();
        for (int l = 0, r = 0; r < s.length(); ++r) {
            char c = s.charAt(r);
            if (map.containsKey(c) && l <= map.get(c)) {
                l = map.get(c) + 1;
            } else {
                ans = Math.max(r - l + 1, ans);
            }
            map.put(c, r);
        }
        return ans;
    }
}
```

## Python 实现

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        l, max_len = 0, 0
        chars_has_seen = dict()
        for r, char in enumerate(s):
            if char in chars_has_seen and l <= chars_has_seen[char]:
                l = chars_has_seen[char] + 1
            else:
                max_len = max(r - l + 1, max_len)
            chars_has_seen[char] = r
        return max_len
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示字符串的长度
- 空间复杂度：$O(\min(n, \,m))$，其中，$n$ 表示字符串的长度，$m$ 表示字符集中字符的数目

# 解法四：滑动窗口（已知字符集）

## 思路

假设我们现在已经知道所有可能出现的字符，比如 `ASCII` 字符集，那么就可以用大小固定的数组代替 `map` 去存储字符的位置。

## Java 实现

```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int ans = 0;
        int[] index = new int[128];
        for (int l = 0, r = 0; r < s.length(); ++r) {
            l = Math.max(index[s.charAt(r)], l);
            ans = Math.max(r - l + 1, ans);
            index[s.charAt(r)] = r + 1;
        }
        return ans;
    }
}
```

## Python 实现

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        all_chars = [0 for _ in range(128)]
        l, max_len = 0, 0
        for r, char in enumerate(s):
            l = max(all_chars[ord(char)], l)  # 得到窗口的左边界
            max_len = max(r - l + 1, max_len)  # 保留最长长度
            all_chars[ord(char)] = r + 1  # 添加/更新字符的位置
        return max_len
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示字符串的长度
- 空间复杂度：$O(\min(n, \,m))$，其中，$n$ 表示字符串的长度，$m$ 表示字符集中字符的数目

