# 445. Add Two Numbers II

[2. Add Two Numbers](charpt1/add_two_numbers.md)

注意：本题目跟第2题类似，区别在于本题的链表前部表示高位，第二题的链表的后部表示高位。

## 1 题目

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

给你两个非空的链表，代表两个非负的整数，链表的每个结点都只含有一个数字（10进制），最高位在链表的头部结点。把这两个数字加起来，以一个链表的形式返回。

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

你可以假设两个数的开头不会含有0， 除非这个链表表示0.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

如果你不能够改变输入的链表（即你不能把链表颠倒，转化为第二题的情况），该如何办。

Example:

Input: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 8 -> 0 -> 7

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/add-two-numbers-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

使用两个栈，把两个链表都读到栈里面去，因为栈是先入后出的。刚好可以把低位先弹出来。但是这种办法的空间复杂度比较高。

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
    	Stack<Integer> stack1 = new Stack();
    	Stack<Integer> stack2 = new Stack();
    	ListNode p = l1;
    	ListNode q = l2;
    	while (p != null) {
    		stack1.push(p.val);
    		p = p.next;
    	}
    	while (q != null) {
    		stack2.push(q.val);
    		q = q.next;
    	}
    	int x = 0, y = 0, carry = 0, sum = 0;
    	ListNode pre = new ListNode(0);
    	while (!stack1.isEmpty() || !stack2.isEmpty()) {
    		x = stack1.isEmpty() ? 0 : stack1.pop();
    		y = stack2.isEmpty() ? 0 : stack2.pop();
    	    sum = x + y + carry;
    	    carry = sum / 10;
    	    ListNode newNode = new ListNode(sum % 10);
    		newNode.next = pre.next;
    		pre.next = newNode;
    	}
        if (carry != 0) {
    		ListNode newNode = new ListNode(carry);
    		newNode.next = pre.next;
    		pre.next = newNode;
    	}
    	return pre.next;
    }
}
```

## 3 解法二

计算两个链表的长度。在长度短的链表前补上值为0的节点。再以相等长度的链表，递归求和。结束时，删除补上的节点。

```java

```

