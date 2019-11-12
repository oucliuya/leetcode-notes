# 234. Palindrome Linked List

## 1 题目



## 2 解法一

半个链表翻转，然后对比。

1. 用两次循环找到链表长度
2. 反转前半部分，刚好可以使得一个指针p到达中间点。
3. 校验回文

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
    public boolean isPalindrome(ListNode head) {
        ListNode p = head;
        ListNode prev = null;
        int len = 0;
        while (p != null) {
        	p = p.next;
        	len++;
        }
        p = head;
        System.out.println(len);
        int move = len / 2;
        while (move > 0) {
        	ListNode nextNode = p.next;
        	p.next = prev;
        	prev = p;
        	p = nextNode;
        	move--;
        }
        if (0 != len % 2 ) 
        	p=p.next;
        boolean res = true;
        while (p != null && prev != null) {
        	if (p.val != prev.val) res = false;
        	p = p.next;
        	prev = prev.next;
        }
        return res;
    }
}
```

## 3 解法二

改进版，快慢指针

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
   public boolean isPalindrome(ListNode head) {
    	ListNode slow = head;
    	ListNode fast = head;
    	while (fast != null && fast.next != null) {
    		slow = slow.next;
    		fast = fast.next.next;
    	}
    	fast = slow;
    	ListNode prev = null;
    	while (fast != null) {
    		ListNode nextNode = fast.next;
    		fast.next = prev;
    		prev = fast;
    		fast = nextNode;
    	}
        while (head != null && prev != null) {
        	if (head.val != prev.val) return false;
        	head = head.next;
        	prev = prev.next;
        }
        return true;
        
    }
}
```

## 4 解法三

改进版，翻转和找中点同时做,而且不计算链表长度

注意：链表长度为奇数or偶数是需要判断的，因为我们获得的后半部分链表的长度可能比前半部分长1 when len为奇数。

我们可以用快指针的值来判断。如果fast == null，则证明链表长度为偶数，前后半长度相等；反之后半部分比前半部分长1。

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
   public boolean isPalindrome(ListNode head) {
    	ListNode slow = head;
    	ListNode fast = head;
    	ListNode prev = null;
    	ListNode curr = head;
    	while (fast != null && fast.next != null) {
    		slow = slow.next;
    		fast = fast.next.next;
    		ListNode nextNode = curr.next;
    		curr.next = prev;
    		prev = curr;
    		curr = nextNode;
    	}
    	if (fast != null)
    		slow = slow.next;
        while (slow != null && prev != null) {
        	if (slow.val != prev.val) return false;
        	slow = slow.next;
        	prev = prev.next;
        }
        return true;
    }
}
```

