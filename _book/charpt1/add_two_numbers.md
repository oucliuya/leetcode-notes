# 2. Add Two numbers

## 1 题目

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

翻译：本题给出两个非空的链表，代表两个非负的整数。数字是按照倒序存储的，每个节点包含一个数字。将两个数字相加，并以链表的形式返回。

你可以假设两个数都不会以0作为开头，除非它本身就是0

**Example:**

```python
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

链接：https://leetcode-cn.com/problems/add-two-numbers

## 2 解法一

**直观思路** 创建一个新链表来存储返回值。对于加数得每一位，将数字相加得一个和。这个和除以10则为进位值，这个和对10取余数则得结果对应位置的数值。

1. 创建dummyNode来存储返回值。它的头节点的值可设为任何值，因为它没用。这里我们设为0
2. 创建一个指针curr指向dummyNode的头部节点
3. 创建储存进位的变量 carry， 进位只能是0或1。因为sum值最大为19，19/10=1=carry； sum<10时，carry为0。
4. 创建两个指针p，q，分别指向l1和l2的头部节点，(不能直接使用l1和l2，因为循环过程中必须保持l1和l2不变)
5. 当q或p没有到达链表尾部的时候，是要做加法的，求的sum，sum的值为x+y+carry。 求出sum之后又可以求出下一位的carry和本位值。
6. carry%10为curr的下一个节点的值，curr记录了下一个节点的值之后向后推进一位。
7. 如果p没有到结尾，则向后推进1位，q也一样。
8. 循环退出后，如果最后一个carry为1，则curr还需再增加一位，存储这个1
9. 最后返回从dummyNode的第二个节点开始的链表(第一个节点是无用节点)

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
		ListNode dummyNode = new ListNode(0);
		ListNode curr = dummyNode;
		int carry = 0;
		ListNode p = l1;
		ListNode q = l2;
		while (p != null || q != null) {
			int x = (p == null)?0:p.val;
			int y = (q == null)?0:q.val;
			int sum = x + y + carry;
			carry = sum / 10;
			curr.next = new ListNode(sum % 10);
			curr = curr.next;
			if (p != null) p = p.next;
			if (q != null) q = q.next;
		}
		if (carry > 0) curr.next = new ListNode(carry);
		return dummyNode.next;
    }
}
```





## 4 相关知识-链表





自己实现一个链表



