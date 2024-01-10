# Contains Cycle

This question is asked by Microsoft. 

> Given a linked list, containing unique numbers, return whether or not it has a cycle.
Note: a cycle is a circular arrangement (i.e. one node points back to a previous node)

Ex: Given the following linked lists...

- 1->2->3->1 -> true (3 points back to 1)
- 1->2->3 -> false
- 1->1 true (1 points to itself)

  LeetCode: https://leetcode.com/problems/linked-list-cycle/

```
public class Solution {
  public boolean hasCycle(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {
      slow = slow.next;
      fast = fast.next.next.next;
      if (slow == fast)
        return true;
    }

    return false;
  }
}
```
