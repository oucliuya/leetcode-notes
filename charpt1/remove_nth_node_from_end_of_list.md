# 19. Remove Nth Node From End of List

## 1 题目

Given a linked list, remove the n-th node from the end of list and return its head.

给一个链表，移除从尾部数第n个节点并返回该链表。

**Example:**

```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given *n* will always be valid.

给定的第n个节点一定是有效地

**Follow up:**

Could you do this in one pass?

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解法1 两次循环

第一次循环：找出链表长度

第二次循环：用一个指针从头开始移动len-n位置，到达应当删除的节点的前一个结点。

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode pre = new ListNode(0);
        pre.next = head;
        ListNode temp = pre;
        int len = 0;
        while (temp.next != null) {
        	len ++;
        	temp = temp.next;
        }
//        System.out.println(len);
        temp = pre;
        for (int i=0; i < len-n; i++) {
        	temp = temp.next;
        }
//        System.out.print(temp.val);
        temp.next = temp.next.next;
        return pre.next;
    }
}
```

## 解法2 一次循环

两个指针start 和 end，初始值都是dummy 结点。 首先将end移动n位。然后将start和end同步向队尾移动，最终当end到达最末尾时，start刚好指向应当删除的结点的前一个结点。

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
            ListNode pre = new ListNode(0);
            pre.next = head;
            ListNode start = pre;
            ListNode end = pre;
            int m = n;
            while (m > 0) {
                end = end.next;
                m--;
            }
    //    	System.out.print(end.val);
            while (end.next != null) {
                start = start.next;
                end = end.next;
            }
    //    	System.out.println(start.val);
            start.next = start.next.next;
            return pre.next;
        }
}
```



