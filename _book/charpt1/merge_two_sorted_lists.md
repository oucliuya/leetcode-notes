# 21. Merge Two Sorted Lists

## 1 题目

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

合并两个有序的列表，并返回一个新列表。这个新列表是由两个列表拼接而成的。

**Example:**

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/merge-two-sorted-lists
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 2 解法一 （递归）

官方解答：

如果``` l1 ```的头部比``` l2```的头部小，则``` l1 ```与 ```l2 ```合并的问题等价为``` l1[1:] ```与```l2```的合并问题；同理 如果 ```l1 ```的头部比```l2```的头部大，那么``` l1 ```与``` l2 ```合并的问题等价为``` l1 ```与 ```l2[1:] ```的合并问题。

终止条件是其中一个链表为空。

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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null) {
            return l2;
        }
        else if (l2 == null) {
            return l1;
        }
        else if (l1.val < l2.val) {
            l1.next = mergeTwoLists(l1.next, l2);
            return l1;
        }
        else {
            l2.next = mergeTwoLists(l1, l2.next);
            return l2;
        }
    }
}
```



## 3 解法二（迭代法）

官方解法：我们新建一个哨兵节点```prehead```, 并维护一个指针```prev```, ```prev```初始化为```prehead```的头部。遍历```l1```和```l2```, ```prev```指向```l1```头部和```l2```头部较小那一个。假如```prev```指向了```l1```的头，那么```l1```往前推进一位，对于```l2```也一样。然后，```prev```也要向前推进一位。这样向前推进，```l1```和```l2```总会有一个到达末尾```null```位置。如果是```l1```先到达了```null```，那么```prev```的下一位只需要指向当前的```l2```即可，反之指向```l1```。

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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode prehead = new ListNode(-1);
        ListNode prev = prehead;
        while (l1 != null && l2 != null) {
            if (l1.val <= l2.val) {
                prev.next = l1;
                l1 = l1.next;
            }
            else {
                prev.next = l2;
                l2 = l2.next;
            }
            prev = prev.next;
        }
        prev.next = l1 == null ? l2 : l1;
        return prehead.next;
    }
}
```



