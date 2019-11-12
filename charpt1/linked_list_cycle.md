# 141. Linked List Cycle

Given a linked list, determine if it has a cycle in it.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

 给你一个链表，判断其中是否有一个环。

为了表示给定链表的环，我们使用一个整数位置```pos```表示链表尾部连接到的结点位置。如果```pos```是```-1```，表示链表中没有环。

Example 1:

Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the second node.

![image](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

Example 2:

Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.

![image](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

Example 3:

Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.

![image](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

**Follow up:**

Can you solve it using *O(1)* (i.e. constant) memory?

能否使得空间复杂度为 *O(1)* 

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/linked-list-cycle
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一

用哈希表存储已经已经遍历过的节点的内存地址，每前进一个结点，都判断哈希表中是否存在该结点的地址，如果存在则说明有环，否则没有。

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
    	HashSet<ListNode> seenNodes = new HashSet<ListNode> ();
    	while (head != null) {
    		if (seenNodes.contains(head)) {
    			return true;
    		}else {
    			seenNodes.add(head);
    			head = head.next;
    		} 		
    	}
    	return false;
    }
}
```

