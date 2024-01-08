# Remove Value

👓This question is asked by Google.👓

> Given a linked list and a value, remove all nodes containing the provided value, and return the resulting list.

Ex: Given the following linked lists and values...

- 1->2->3->null, value = 3, return 1->2->null
- 8->1->1->4->12->null, value = 1, return 8->4->12->null
- 7->12->2->9->null, value = 7, return 12->2->9->null

LeetCode: https://leetcode.com/problems/remove-linked-list-elements/

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode current = dummy;
        while (current.next != null) {
            if (current.next.val == val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return dummy.next;
    }
    
}
```
