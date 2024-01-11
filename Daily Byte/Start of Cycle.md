#  Start of Cycle

This question is asked by Apple.

> Given a potentially cyclical linked list where each value is unique, return the node at which the cycle starts. If the list does not contain a cycle, return null.

Ex: Given the following linked lists...

- 1->2->3, return null
- 1->2->3->4->5->2 (5 points back to 2), return a reference to the node containing 2
- 1->9->3->7->7 (7 points to itself), return a reference to the node containing 7

LeetCode: https://leetcode.com/problems/linked-list-cycle-ii/

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
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) break;
        }
        if (fast == null || fast.next == null) return null;
        while (head != slow) {
            head = head.next;
            slow = slow.next;
        }
        return head;
    }
}


```
