# Find Middle Element

🌴This question is asked by Amazon.🌴

> Given a non-empty linked list, return the middle node of the list. If the linked list contains an even number of elements, return the node closer to the end.

Ex: Given the following linked lists...

- 1->2->3->null, return 2
- 1->2->3->4->null, return 3
- 1->null, return 1

  LeetCode: https://leetcode.com/problems/middle-of-the-linked-list/description/
  
  ```java
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
