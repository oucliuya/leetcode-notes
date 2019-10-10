# 23. Merge k Sorted Lists

## 1 题目

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

合并k个有序的链表，返回一个新的有序列表。分析复杂度。

**Example:**

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/merge-k-sorted-lists
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

暴力法：

1. 遍历所有链表的所有元素，把它们都取出来放在一个数组里
2. 对这个数组进行排序
3. 遍历这个数组，取出每个元素拼接到一个新的链表中

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
    public ListNode mergeKLists(ListNode[] lists) {
        
    }
}
```

## 3 解法二

我们在第21题中已经得到了如何合并两个链表的方法，这个问题只需两两合并所有链表即可。两两合并有两种办法

拿第一个链表跟第二个合并，用其结果跟第三个合并，直到最后一个链表。这种办法需要合并 N-1 次。（无论用什么组合的方式，要最终得到一个链表，合并次数都是N-1次）

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
    public ListNode mergeKLists(ListNode[] lists) {
        if (lists.length < 1) {
            return null;
        }
		ListNode p = lists[0];
		for (int i = 1; i < lists.length; i++) {
			p = mergeTwoListNode(p, lists[i]);
		}
		return p;        
    }
    
	public static ListNode mergeTwoListNode(ListNode l1, ListNode l2) {
		ListNode prehead = new ListNode(-1);
		ListNode prev = prehead;
		while (l1 != null && l2 != null) {
			if (l1.val <= l2.val) {
				prev.next = l1;
				l1 = l1.next;
			}
			else {
				prev.next = l2;
				l2 = l2.next;
			}
			prev = prev.next;
		}
		prev.next = l1 == null ? l2 : l1;
		return prehead.next;
	}
}
```

