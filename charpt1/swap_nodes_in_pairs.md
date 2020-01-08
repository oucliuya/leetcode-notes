# 24. Swap Nodes in Pairs

## 1 题目

Given a linked list, swap every two adjacent nodes and return its head.

You may not modify the values in the list's nodes, only nodes itself may be changed.

给一个链表，把每两个相邻的节点颠倒，返回这个链表的头。你不能修改链表结点的值，而是对结点进行操作。

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/swap-nodes-in-pairs
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解法1 递归

终止条件：轮询到了链表的末尾。既 head==null || head.next ==null

每次调用的操作：交换本结点和下一个结点

返回值：next结点

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
      ListNode nextNode = head.next;
      head.next = swapPairs(nextNode.next);
      nextNode.next = head;
      return nextNode;
    }
}
```

## 解法2 非递归

使用双指针，start和end指向要交换的连个元素。 但是不要忘记，我们还需要使用一个指针来遍历整个链表，也就是code里的temp指针。

循环终止条件：start指针和end指针都不为null。

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
        ListNode pre = new ListNode(0);
        pre.next = head;
        ListNode temp = pre;
        while (temp.next != null && temp.next.next != null) {
          ListNode start = temp.next;
            ListNode end = start.next;
            start.next = end.next;
            end.next = start;
            temp.next = end;
            temp = start;
        }
        return pre.next;
      }
}
```

