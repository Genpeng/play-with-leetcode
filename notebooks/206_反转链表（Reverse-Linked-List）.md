> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

反转一个单链表。

**示例**：

```
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

**进阶**：
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？

# 解法一：迭代

## 思路

遍历链表的每个节点，将每个节点的 `next` 指针指向它的前一个节点（即前驱）。因为这是一个单向链表，并不存在指向前一个节点的引用，因此需要一个变量存储指向前一个节点的引用。同时，在改变节点的 `next` 指针之前，还需要另一个变量存储指向下一个节点的引用。

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
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode cur = head;
        while (cur != null) {
        	ListNode nextNode = cur.next;
        	cur.next = prev;
        	prev = cur;
        	cur = nextNode;
        }
        return prev;
    }
}
```

## Python 实现

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        prev, curr = None, head
        while curr:
            curr.next, prev, curr = prev, curr, curr.next
        return prev
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示链表的节点数
- 空间复杂度：$O(1)$

# 解法二：递归

## 思路

递归的思路和迭代的方式相反，递归是从链表的尾节点（tail）开始逐一改变节点的 `next` 指针。因此，递归的方式首先会递归到链表的尾节点，此时递归的深度为 $n$ （$n$ 表示链表的节点数），然后再逐层返回，每次都修改当前节点的 `next` 指针。

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
    public ListNode reverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        
        ListNode p = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return p;
    }
}
```

## Python 实现

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head == None or head.next == None:
            return head
        
        p = self.reverseList(head.next)
        head.next.next, head.next = head, None
        return p  
```

## 复杂度分析

- 时间复杂度：$O(n)$，其中 $n$ 表示链表的节点数
- 空间复杂度：$O(n)$，额外的空间是由于递归调用占用系统栈的空间，递归的深度最多为 $n$ 层