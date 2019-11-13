# 82. Remove Duplicates from Sorted List II

[参考 83. Remove Duplicates from Sorted List](charpt1/remove_duplicates_from_sorted_list.md)

## 1 题目

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

给一个有序的链表，删除所有含有重复数字的节点。只留下无重复的数字。注意：重复字符全部去掉，而不是留下一个。

Example 1:

Input: 1->2->3->3->4->4->5
Output: 1->2->5
Example 2:

Input: 1->1->1->2->3
Output: 2->3

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

使用快慢指针，快指针遍历整个链表。慢指针来做删除。

1. fast遍历链表
2. 如果fast的下一个值与本值相等，判断是否需要删结点。 如果slow指向fast，那么slow移动到fast；否则slow指向fast的下一个结点，把其间的重复节点都删掉。
3. 如果fast的下一个值和本值相同。slow直接指向 fast的下一个的下一个。从而做到把重复值删掉

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
    	ListNode fast = head;
    	ListNode slow = pre;
    	while (fast != null && fast.next != null) {
    		if (fast.val != fast.next.val) {
    			if(slow.next == fast) {
    				slow = fast;
    			}else {
    				slow.next = fast.next;
    			}
    		}else {
    			slow.next = fast.next.next;
    		}
    		fast = fast.next;
    	}
    	return pre.next;
    }
}
```

