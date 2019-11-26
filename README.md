# 我的 LeetCode 刷题之旅
![努力奋斗](./figs/努力奋斗.png)

[TOC]

## 前言

这是我的 LeetCode 题解笔记。说来惭愧，从学生时代到进入社会，都没有在 LeetCode 上刷过算法题（只刷过《剑指 offer》之类的）。因此，为了弥补遗憾，也为了夯实自己的数据结构和算法基础，所以决定工作之余利用闲暇时间刷刷 LeetCode 的算法题。一方面可以捡起数据结构和算法，另一方面也可以锻炼自己解决问题的能力。

因为自己的题解笔记中包含少量的 LaTeX 公式，如果直接打开可能无法正确显示，因此将笔记的搬到了 CSDN 博客上，读者可以直接点击题目，会自动跳转到相应的文章去。所有的笔记都在 [notebooks](https://github.com/Genpeng/play-with-leetcode/tree/master/notebooks) 文件夹下，感兴趣的读着也可以 clone 下来看。

可以保证的是，所有的题目都是可以正确通过的，而且基本上每道题笔者都会给出多种解法。因为自己水平有限，如果描述有误的，不吝指出，万分感激。

后记：刷着刷着自己确实上瘾了，每天如果有空一定要刷刷题才觉得有意思，也算是别样的乐趣吧。

## 题解笔记

| #    | 题名                                                         | 标签                 | 解答                                                         | 难度 |
| ---- | ------------------------------------------------------------ | -------------------- | ------------------------------------------------------------ | ---- |
| 1    | 两数之和                                                     | 数组,哈希表          | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/array/leetcode1/Solution.java),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc1/solution.py) | 简单 |
| 2    | [两数相加](https://blog.csdn.net/x273591655/article/details/83013740) | 链表                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc2),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc2/solution.py) | 中等 |
| 7    | [反转整数](https://blog.csdn.net/x273591655/article/details/83178569) | 数学                 |                                                              | 简单 |
| 9    | [回文数](https://blog.csdn.net/x273591655/article/details/83578572) | 数学                 |                                                              | 简单 |
| 20   | [有效的括号](https://blog.csdn.net/x273591655/article/details/83500912) | 字符串,栈            |                                                              | 简单 |
| 21   | [合并两个有序链表](https://blog.csdn.net/x273591655/article/details/83380899) | 链表                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc21),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc21/solution.py) | 简单 |
| 54   | 螺旋矩阵                                                     | 数组                 |                                                              | 中等 |
| 61   | [旋转链表](https://blog.csdn.net/x273591655/article/details/83784151) | 链表,双指针          |                                                              | 中等 |
| 66   | 加一                                                         | 数组,数学            | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/lc66/Solution.java),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc66/solution.py) | 简单 |
| 94   | [二叉树的中序遍历](https://blog.csdn.net/x273591655/article/details/83027962) | 树,二叉树            |                                                              | 简单 |
| 102  | 二叉树的层序遍历                                             | 树,二叉树            |                                                              | 简单 |
| 136  | [只出现一次的数字](https://blog.csdn.net/x273591655/article/details/83268930) | 数组,Map,数学,位运算 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/lc136/Solution4.java),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc136/solution.py) | 简单 |
| 141  | [环形链表](https://blog.csdn.net/x273591655/article/details/83343679) | 链表,双指针          | [Java](<https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc141>),[Python](<https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc141/solution.py>) | 简单 |
| 142  | [环形链表Ⅱ](https://blog.csdn.net/x273591655/article/details/83759373) | 链表,双指针          | [Java](<https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc142>),[Python](<https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc142/solution.py>) | 中等 |
| 160  | [相交链表](https://blog.csdn.net/x273591655/article/details/83759373) | 链表,双指针          | [Java](<https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc160>),[Python](<https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc160/solution.py>) | 简单 |
| 169  | [求众数](https://blog.csdn.net/x273591655/article/details/83574810) | 数组                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc169),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc169/solution.py) | 简单 |
| 203  | [移除链表元素](<https://github.com/Genpeng/play-with-leetcode/blob/master/notebooks/203_Removed-Linked-List-Elements.md>) | 链表                 | [Java](<https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/lc203/Solution.java>),[Python](<https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc203/solution.py>) | 简单 |
| 206  | [反转链表](https://blog.csdn.net/x273591655/article/details/83306135) | 链表                 | [Java](<https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc206>),[Python](<https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc206/solution.py>) | 简单 |
| 231  | [2的幂](https://blog.csdn.net/x273591655/article/details/83715198) | 数学                 |                                                              | 简单 |
| 237  | [删除链表中的节点](https://blog.csdn.net/x273591655/article/details/83374572) | 链表                 |                                                              | 简单 |
| 349  | [两个数组的交集](https://blog.csdn.net/x273591655/article/details/83058256) | 数组                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc349),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc349/solution.py) | 简单 |
| 350  | [两个数组的交集Ⅱ](https://blog.csdn.net/x273591655/article/details/83060347) | 数组                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc350),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc350/solution.py) | 简单 |
| 498  | 对角线遍历                                                   | 数组                 |                                                              | 中等 |
| 530  | [二分搜索树的最小绝对值差](https://blog.csdn.net/x273591655/article/details/82999627) | 树,二分搜索树        |                                                              | 简单 |
| 724  | 寻找数组的中心索引                                           | 数组                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/lc724/Solution.java),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc724/solution.py) | 简单 |
| 747  | 至少是其他数字两倍的最大数                                   | 数组                 | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/lc747/Solution.java),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc747/solution.py) | 简单 |
| 804  | 唯一的摩尔斯密码词                                           | 集合                 |                                                              | 简单 |
| 19   | [删除链表的倒数第N个节点](https://blog.csdn.net/x273591655/article/details/83825297) | 链表,双指针          |                                                              | 中等 |
| 347  | [前K个高频元素](https://blog.csdn.net/x273591655/article/details/84001236) | 堆,队列,优先队列     |                                                              | 中等 |
| 24   | [两两交换链表中的节点](https://blog.csdn.net/x273591655/article/details/84330800) | 链表                 |                                                              | 中等 |
| 25   | [k个一组翻转链表](https://blog.csdn.net/x273591655/article/details/84558566) | 链表                 |                                                              | 困难 |
| 844  | [比较含退格的字符串](https://blog.csdn.net/x273591655/article/details/84595069) | 栈,双指针            |                                                              | 简单 |
| 232  | [用栈实现队列](https://blog.csdn.net/x273591655/article/details/84680072) | 栈,队列              |                                                              | 简单 |
| 225  | [用队列实现栈](https://blog.csdn.net/x273591655/article/details/84729232) | 栈,队列              |                                                              | 简单 |
| 692  | 前K个高频单词                                                | 堆,优先队列          |                                                              | 中等 |
| 703  | 数据流中的第K大元素                                          | 堆,优先队列          |                                                              | 简单 |
| 283  | 移动零                                                       | 数组,双指针          | [Java](https://github.com/Genpeng/leetcode-challenges-with-java/tree/master/src/lc283),[Python](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/lc283/solution.py) | 简单 |
| 3    | [无重复字符的最长子串](https://blog.csdn.net/x273591655/article/details/84958536) | 字符串,双指针        |                                                              | 中等 |

TODO：添加 C++ 语言的解答

## 数组专题

| #    | 题名 | 难度 | 标签 | C++ 解答 | Java 解答 | Python 解答 |
| ---- | ---- | :--: | :--: | :------: | :-------: | :---------: |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |

## 字符串专题

| #    | 题名           | 难度 |    标签    | C++ 解答 |                          Java 解答                           |                         Python 解答                          |
| ---- | -------------- | :--: | :--------: | :------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 890  | 查找和替换模式 | 中等 | string,map |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/string/lc0890_find_and_replace_pattern/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/string/lc0890_find_and_replace_pattern/Solution2.java),[[3]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/string/lc0890_find_and_replace_pattern/Solution3.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/string/lc0890_find_and_replace_pattern/solution.py) |
|      |                |      |            |          |                                                              |                                                              |
|      |                |      |            |          |                                                              |                                                              |
|      |                |      |            |          |                                                              |                                                              |
|      |                |      |            |          |                                                              |                                                              |
|      |                |      |            |          |                                                              |                                                              |

## 链表专题

| #    | 题名                                                         | 难度   | 标签                                | C++ 解答 | Java 解答                                                    | Python 解答                                                  |
| ---- | ------------------------------------------------------------ | ------ | ----------------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 2    | [Add Two Numbers](https://blog.csdn.net/x273591655/article/details/83013740) | Medium | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0002_add_two_numbers/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0002_add_two_numbers/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0002_add_two_numbers/solution.py) |
| 19   | [Remove Nth Node From End of List](https://blog.csdn.net/x273591655/article/details/83825297) | Medium | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0019_remove_nth_node_from_end_of_list/Solution.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0019_remove_nth_from_end_of_list/solution.py) |
| 21   | [Merge Two Sorted Lists](https://blog.csdn.net/x273591655/article/details/83380899) | Easy   | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0021_merge_two_sorted_lists/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0021_merge_two_sorted_lists/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0021_merge_two_sorted_lists/solution.py) |
| 23   | Merge k Sorted Lists                                         | Hard   | linked list,divide and conquer,heap |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution2.java),[[3]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution3.java),[[4]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution4.java),[[5]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution5.java),[[6]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0023_merge_k_sorted_lists/Solution6.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0023_merge_k_sorted_lists/solution.py) |
| 24   | [Swap Nodes in Pairs](https://blog.csdn.net/x273591655/article/details/84330800) | Medium | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0024_swap_nodes_in_pairs/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0024_swap_nodes_in_pairs/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0024_swap_nodes_in_pairs/solution.py) |
| 61   | [Rotate List](https://blog.csdn.net/x273591655/article/details/83784151) | Medium | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0061_rotate_list/Solution.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0061_rotate_list/solution.py) |
| 141  | [Linked List Cycle](https://blog.csdn.net/x273591655/article/details/83343679) | Easy   | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0141_linked_list_cycle/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0141_linked_list_cycle/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0141_linked_list_cycle/solution.py) |
| 142  | [Linked List Cycle II](https://blog.csdn.net/x273591655/article/details/83759373) | Medium | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0142_linked_list_cycle_ii/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0142_linked_list_cycle_ii/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0142_linked_list_cycle_ii/solution.py) |
| 148  | Sort List                                                    | Medium | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0148_sort_list/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0148_sort_list/Solution2.java),[[3]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0148_sort_list/Solution3.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0148_sort_list/solution.py) |
| 160  | [Intersection of Two Linked List](https://blog.csdn.net/x273591655/article/details/83759373) | Easy   | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0160_intersection_of_two_linked_list/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0160_intersection_of_two_linked_list/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0160_intersection_of_two_linked_lists/solution.py) |
| 203  | [Remove Linked List Elements](https://github.com/Genpeng/play-with-leetcode/blob/master/notebooks/203_Removed-Linked-List-Elements.md) | Easy   | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0203_remove_linked_list_elements/Solution.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0203_remove_linked_list_elements/solution.py) |
| 206  | [Reverse Linked List](https://blog.csdn.net/x273591655/article/details/83306135) | Easy   | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0206_reverse_linked_list/Solution1.java),[[2]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0206_reverse_linked_list/Solution2.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0206_reverse_linked_list/solution.py) |
| 237  | [Delete Node in a Linked List](https://blog.csdn.net/x273591655/article/details/83374572) | Easy   | linked list                         |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0237_delete_node_in_a_linked_list/Solution.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0237_delete_node_in_a_linked_list/solution.py) |
| 876  | Middle of the Linked List                                    | Easy   | linked list,two pointers            |          | [[1]](https://github.com/Genpeng/leetcode-challenges-with-java/blob/master/src/linked_list/lc0876_middle_of_the_linked_list/Solution.java) | [solution](https://github.com/Genpeng/leetcode-challenges-with-python/blob/master/PyLeetCode/linked_list/lc0876_middle_of_the_linked_list/solution.py) |

## 树专题

| #    | 题名                                                         | 难度   | 标签     | C++ 解答 | Java 解答 | Python 解答 |
| ---- | ------------------------------------------------------------ | ------ | -------- | -------- | --------- | ----------- |
| 236  | [二叉树的最近公共祖先](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree) | Medium | tree,dfs |          |           |             |
|      |                                                              |        |          |          |           |             |
|      |                                                              |        |          |          |           |             |
|      |                                                              |        |          |          |           |             |
|      |                                                              |        |          |          |           |             |

## 动态规划专题

| #    | 题名 | 难度 | 标签 | C++ 解答 | Java 解答 | Python 解答 |
| ---- | ---- | ---- | ---- | -------- | --------- | ----------- |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |
|      |      |      |      |          |           |             |