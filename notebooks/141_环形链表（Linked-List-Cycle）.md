> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

给定一个链表，判断链表中是否有环。

**进阶：**
你能否不使用额外空间解决此题？

# 解法一：哈希表

## 思路

判断一个链表是否包含环，可以转化为判断是否有一个节点之前已经出现过。非常自然的一个想法就是：遍历链表的每个节点，用一个哈希表记录每个节点的引用（或内存地址）；如果能够遍历到空节点，则此时已经遍历到链表的尾部，返回 `false`；如果有一个节点的引用出现在哈希表中，则返回 `true`。

## Java 实现

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        Set<ListNode> nodesSeen = new HashSet<>();
        while (head != null) {
            if (nodesSeen.contains(head)) {
                return true;
            }
            nodesSeen.add(head);
            head = head.next;
        }
        return false;
    }
}
```


## Python 实现

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        nodes_seen = set()
        while head:
            if head in nodes_seen:
                return True
            nodes_seen.add(head)
            head = head.next
        return False
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 为链表的节点数，因为哈希表的查找和添加操作的时间复杂度是 $O(1)$ 的，所以整体的时间复杂度是 $O(n)$ 的
- 空间复杂度：$O(n)$，最多只需要保存 $n$ 个节点的引用

# 解法二：双指针（龟兔算法）

## 思路

另一种思路就是采用 *Floyd* 的[**龟兔算法**](https://en.wikipedia.org/wiki/Cycle_detection#Floyd's_Tortoise_and_Hare)，即借用两个指针，一个快指针和一个慢指针，快指针每次移动两个节点而慢指针则每次移动一个节点。如果链表中不存在环，则快指针会先于慢指针到达链表的尾部，两个指针永远也不可能“相遇”；相反，如果链表中存在环，则快指针一定会“追上”慢指针，就如同龟兔赛跑一样，速度快的兔子一定会追上乌龟。

## Java 实现

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            
            if (fast == slow) {
                return true;
            }
        }
        return false;
    }
}
```


## Python 实现

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        slow, fast = head, head
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
            if fast == slow:
                return True
        return False
# Runtime: 40 ms
# Your runtime beats 100.00 % of python submissions.
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 为链表的节点数，按照链表中是否存在环，分两种情况进行讨论：
  1. 链表中不存在环：快指针会优先到达链表尾部（最多只需要 $n/2$ 次），时间复杂度为 $O(n)$
  2. 链表中存在环：我们可以把慢指针的移动分解成两个部分，“直线“部分和”环形“部分。对于”直线“部分，假设链表中”直线“部分的长度为 $N$，则慢指针只需 $N$ 次迭代便可到达”环形“部分，此时快指针已经进入了”环形“部分；对于”环形“部分，假设链表中”环形“部分的长度为 $K$，由于两个指针的速度之差为 1，因此最坏的情况下，经过 $K$ 次迭代后快指针便能”追上“慢指针。综上，最坏情况下的时间复杂度为 $O(N + K) = O(n)​$

- 空间复杂度：$O(1)$，只需要存储两个节点的引用