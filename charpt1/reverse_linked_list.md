# 206. Reverse Linked List

## 1 题目

Reverse a singly linked list.

**Example:**

```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

Follow up:

A linked list can be reversed either iteratively or recursively. Could you implement both?

分别使用迭代和递归法来做。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/reverse-linked-list
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 迭代法

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
    	ListNode curr = head;
    	while (curr != null) {
    		ListNode nextNode = curr.next;  // 此时应该先把下一个点取出来，否则下一步curr变了。
    		curr.next = prev;
    		prev = curr;
    		curr = nextNode;
    	}
    	return prev;
    }
}
```

## 3 递归法

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
    	ListNode temp = reverseList(head.next);
    	head.next.next = head;
    	head.next = null;
    	return temp;
    }    
}
```



