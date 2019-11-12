# 876. Middle of the Linked List

## 1 题目

Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.

```
Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
```

```
Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/middle-of-the-linked-list
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

直观解法：两次循环。第一次遍历整个链表，找到长度；第二次遍历半个链表，找到后半部分的起点。

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
    public ListNode middleNode(ListNode head) {
        ListNode temp = head;
        int len = 0;
        while(temp != null) {
            temp = temp.next;
            len++;
        }
        // System.out.println(len);
        temp = head;
        len /= 2;
        while (len > 0) {
            temp = temp.next;
            len--;
        }
        return temp;
    }
}
```

## 3 解法二

快慢指针

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
    public ListNode middleNode(ListNode head) {
    	ListNode slow = head;
    	ListNode fast = head;
    	while (fast != null && fast.next != null) {
    		slow = slow.next;
    		fast = fast.next.next;
    	}
    	return slow;
    }
}
```

