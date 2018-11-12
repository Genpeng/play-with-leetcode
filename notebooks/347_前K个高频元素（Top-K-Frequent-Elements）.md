> 更多 LeetCode 题解笔记可以访问我的 [github](https://github.com/Genpeng/play-with-leetcode)。

[TOC]

# 描述

给定一个非空的整数数组，返回其中出现频率前 **k** 高的元素。

**示例 1:**

```
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```

**示例 2:**

```
输入: nums = [1], k = 1
输出: [1]
```

**说明：**

- 你可以假设给定的 *k* 总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
- 你的算法的时间复杂度**必须**优于 O(*n* log *n*) , *n* 是数组的大小。

# 解法一：排序算法（不满足时间复杂度要求）

拿到题目的时候，如果没有详细看说明的话，一般都会首先想到使用排序算法对元素按照频率由高到低进行排序，然后取前 $k$ 个元素。但是这样做的时间复杂度是 $O(n\log{n})$ 的， 不满足题目要求。虽然不满足题目要求，但是还是将求解程序写一下。

**备注**：在 LeetCode 中的运行时间也不是特别慢。

## Java 实现

```java
import java.util.Map;
import java.util.HashMap;
import java.util.List;
import java.util.ArrayList;

class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        // 统计元素的频率
        Map<Integer, Integer> freqMap = new HashMap<>();
        for (int num : nums) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }
        
        // 对元素按照频率进行降序排序
        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(freqMap.entrySet());
        Collections.sort(list, new Comparator<Map.Entry<Integer, Integer>>() {
            @Override
            public int compare(Map.Entry<Integer, Integer> o1, Map.Entry<Integer, Integer> o2) {
                return o2.getValue() - o1.getValue();
            }
        });
        
        // 取出前k个元素
        int count = 0;
        List<Integer> ret = new ArrayList<>();
        for (Map.Entry<Integer, Integer> entry : list) {
            ret.add(entry.getKey());
            ++count;
            if (count >= k) {
                break;
            }
        }
        return ret;
    }
}
// Runtime: 18 ms
// Your runtime beats 62.23 % of java submissions.
```

## Python 实现

```python
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        # 统计元素的频率
        freq_dict = dict()
        for num in nums:
            freq_dict[num] = freq_dict.get(num, 0) + 1
            
        # 按照频率进行排序
        freq_dict_sorted = sorted(freq_dict.items(), key=lambda x: x[1], reverse=True)
        
        # 取前k个元素返回
        ret = list()
        for i in range(k):
            ret.append(freq_dict_sorted[i][0])
        return ret
# Runtime: 52 ms
# Your runtime beats 71.83 % of python3 submissions.
```

## 复杂度分析

- **时间复杂度**：$O(n\log{n})$，其中 $n$ 表示数组的长度。
- **空间复杂度**：$O(n)$，最极端的情况下（每个元素都不同），用于存储元素及其频率的 Map 需要存储 $n$ 个键值对

# 解法二：最小堆

## 思路

进一步，为了满足时间复杂度要求，需要对解法一的排序过程进行改进。因为最终需要返回前 $k$ 个频率最大的元素，可以想到借助堆这种数据结构。通过维护一个元素数目为 $k$ 的最小堆，每次都将新的元素与堆顶端的元素（堆中频率最小的元素）进行比较，如果新的元素的频率比堆顶端的元素大，则弹出堆顶端的元素，将新的元素添加进堆中。最终，堆中的 $k$ 个元素即为前 $k$ 个高频元素。

## Java 实现

```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        // 统计元素的频率
        Map<Integer, Integer> map = new HashMap<>(16);
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        // 遍历map，用最小堆保存频率最大的k个元素
        PriorityQueue<Integer> pq = new PriorityQueue<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer a, Integer b) {
                return map.get(a) - map.get(b);
            }
        });
//        PriorityQueue<Integer> pq = new PriorityQueue<>(
//                (a, b) -> map.get(a) - map.get(b)
//        );
        for (Integer key : map.keySet()) {
            if (pq.size() < k) {
                pq.add(key);
            } else if (map.get(key) > map.get(pq.peek())) {
                pq.remove();
                pq.add(key);
            }
        }

        // 取出最小堆中的元素
        List<Integer> ret = new ArrayList<>();
        while (!pq.isEmpty()) {
            ret.add(pq.remove());
        }

        return ret;
    }
}
```

## Python 实现

```python
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        # 统计元素的频率
        freq_dict = dict()
        for num in nums:
            freq_dict[num] = freq_dict.get(num, 0) + 1
            
        # 维护一个大小为k的最小堆，使得堆中的元素即为前k个高频元素
        pq = list()
        for key, value in freq_dict.items():
            if len(pq) < k:
                heapq.heappush(pq, (value, key))
            elif value > pq[0][0]:
                heapq.heapreplace(pq, (value, key))
                
        # 取出堆中的元素
        ret = list()
        while pq:
            ret.append(heapq.heappop(pq)[1])
        return ret
```

## 复杂度分析

- **时间复杂度**：$O(n\log{k})$，其中 $n$ 表示数组的长度。首先，遍历一遍数组统计元素的频率，这一系列操作的时间复杂度是 $O(n)$ 的；接着，遍历用于存储元素频率的 map，如果元素的频率大于最小堆中顶部的元素，则将顶部的元素删除并将该元素加入堆中，这一系列操作的时间复杂度是 $O(n\log{k})$ 的；最后，弹出堆中的元素所需的时间复杂度是 $O(k\log{k})$ 的。因此，总的时间复杂度是 $O(n\log{k})$ 的。
- **空间复杂度**：$O(n)$，最坏情况下（每个元素都不同），map 需要存储 $n$ 个键值对，优先队列需要存储 $k$ 个元素，因此，空间复杂度是 $O(n)$ 的。

# 解法三：桶排序（bucket sort）

## 思路

最后，为了进一步优化时间复杂度，可以采用桶排序（bucket sort），即用空间复杂度换取时间复杂度。

第一步和解法二相同，也是统计出数组中元素的频次。接着，将数组中的元素按照出现频次进行分组，即出现频次为 $i$ 的元素存放在第 $i$ 个桶。最后，从桶中逆序取出前 $k$ 个元素。

## Java 实现

```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        // 统计元素的频次
        Map<Integer, Integer> int2FreqMap = new HashMap<>(16);
        for (int num : nums) {
            int2FreqMap.put(num, int2FreqMap.getOrDefault(num, 0) + 1);
        }
        
        // 桶排序
        List<Integer>[] bucket = new List[nums.length + 1];
        for (Integer key : int2FreqMap.keySet()) {
            int freq = int2FreqMap.get(key);
            if (bucket[freq] == null) {
                bucket[freq] = new ArrayList<>();
            }
            bucket[freq].add(key);
        }
        
        // 逆序（频次由高到低）取出元素
        List<Integer> ret = new ArrayList<>();
        for (int i = nums.length; i >= 0 && ret.size() < k; --i) {
            if (bucket[i] != null) {
                ret.addAll(bucket[i]);
            }
        }
        
        return ret;
    }
}
```

## Python 实现

```python
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        # 统计元素的频率
        freq_dict = dict()
        for num in nums:
            freq_dict[num] = freq_dict.get(num, 0) + 1

        # 桶排序
        bucket = [[] for _ in range(len(nums) + 1)]
        for key, value in freq_dict.items():
            bucket[value].append(key)

        # 逆序取出前k个元素
        ret = list()
        for i in range(len(nums), -1, -1):
            if bucket[i]:
                ret.extend(bucket[i])
            if len(ret) >= k:
                break
        return ret[:k]
```

## 复杂度分析

- **时间复杂度**：$O(n)$，其中 $n$ 表示数组的长度。
- **空间复杂度**：$O(n)$
