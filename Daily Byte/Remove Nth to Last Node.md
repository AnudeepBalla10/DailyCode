# Remove Nth to Last Node

📖This question is asked by Facebook.📖

> Given a linked list and a value n, remove the nth to last node and return the resulting list.

Ex: Given the following linked lists...

- 1->2->3->null, n = 1, return 1->2->null
- 1->2->3->null, n = 2, return 1->3->null
- 1->2->3->null, n = 3, return 2->3->null

LeetCode: https://leetcode.com/problems/remove-nth-node-from-end-of-list/


  ```Java
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode start = new ListNode();
        start.next = head;
        ListNode fast = start;
        ListNode slow = start;     

        for(int i = 1; i <= n; ++i)
            fast = fast.next;
    
        while(fast.next != null)
        {
            fast = fast.next;
            slow = slow.next;
        }
        
        slow.next = slow.next.next;
        
        return start.next;     
    }
}
  ```
