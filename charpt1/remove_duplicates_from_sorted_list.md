# 83. Remove Duplicates from Sorted List II

## 1 题目

Given a sorted linked list, delete all duplicates such that each element appear only once.

给一个排好序的链表，删除所有重复的节点，使得每个值只出现一次。

**Example 1:**

```
Input: 1->1->2
Output: 1->2
```

**Example2:**

```
Input: 1->1->2->3->3
Output: 1->2->3
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法1 直观遍历

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
    public ListNode deleteDuplicates(ListNode head) {
    	ListNode pre = new ListNode(0);
    	pre.next = head;
    	ListNode temp = pre.next;
    	while (temp != null && temp.next != null) {
    		while (temp.next != null && temp.val == temp.next.val) 
    			temp.next = temp.next.next;
    		temp = temp.next;
    	}
    	return pre.next;
    }
}
```

