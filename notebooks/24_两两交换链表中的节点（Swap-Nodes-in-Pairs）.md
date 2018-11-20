> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

**示例:**

```
给定 1->2->3->4, 你应该返回 2->1->4->3.
```

**说明:**

- 你的算法只能使用常数的额外空间。
- **你不能只是单纯的改变节点内部的值**，而是需要实际的进行节点交换。

# 解法一：迭代

## 思路

这道题的思路其实很直接（改变一对节点的 `next` 指针），比较难的是该如何进行交换。这里，我首先生成一个虚拟头节点 `dummy`，这样可以将后面执行的操作统一起来，不用区分是否为链表的头部（head）。接着，借助于两个指针 `first` 和 `second`，实现两个节点的“交换”。

## Java 实现

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode curr = dummy;
        while (curr.next != null && curr.next.next != null) {
            ListNode first = curr.next;
            ListNode second = curr.next.next;
            
            // swap two nodes
            first.next = second.next;
            second.next = first;
            curr.next = second;
            
            // update to next iteration
            curr = curr.next.next;
        }
        return dummy.next;
    }
}
// Runtime: 2 ms
// Your runtime beats 100.00 % of java submissions.
```

## Python 实现

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        dummy = ListNode(-1)
        dummy.next, curr = head, dummy
        while curr.next and curr.next.next:
            first, second = curr.next, curr.next.next
            
            # swap two nodes
            first.next, second.next, curr.next = second.next, first, second
            
            # update to next iteration
            curr = curr.next.next
        return dummy.next
# Runtime: 32 ms
# Your runtime beats 100.00 % of python3 submissions.
```

## 复杂度分析

- **时间复杂度**：$O(n)$，其中 $n$ 表示链表的长度（节点的数目）。循环需要的次数为 $\left \lfloor \frac{n}{2} \right \rfloor$，且循环中执行的操作的时间复杂度为 $O(1)$，因此，总的时间复杂度是 $O(n)$。
- **空间复杂度**：$O(1)$，只需要存储 4 个节点的引用和一个虚拟头结点。

# 解法二：递归（不满足空间复杂度要求）

## 思路

递归的方式也需要改变一对节点的 `next` 指针，不同的是，递归的方式首先递归到链表的尾部，然后从链表的尾部开始交换节点，一直到链表的头部。

## Java 实现

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode p = head.next;
        head.next = swapPairs(head.next.next);
        p.next = head;
        return p;
    }
}
// Runtime: 2 ms
// Your runtime beats 100.00 % of java submissions.
```

## Python 实现

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head
        p = head.next
        head.next = self.swapPairs(head.next.next)
        p.next = head
        return p
```

## 复杂度分析

- **时间复杂度**：$O(n)$，其中 $n$ 表示链表的长度（节点的数目）。
- **空间复杂度**：$O(n)$，递归调用占用系统栈空间，递归的深度为 $\left \lfloor \frac{n}{2} \right \rfloor$。