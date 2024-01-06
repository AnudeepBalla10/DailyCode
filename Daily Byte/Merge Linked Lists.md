# Merge Linked Lists

This question is asked by Apple. 

>Given two sorted linked lists, merge them together in ascending order and return a reference to the merged list

Ex: Given the following lists...

- list1 = 1->2->3, list2 = 4->5->6->null, return 1->2->3->4->5->6->null
- list1 = 1->3->5, list2 = 2->4->6->null, return 1->2->3->4->5->6->null
- list1 = 4->4->7, list2 = 1->5->6->null, return 1->4->4->5->6->7->null


Leetcode: https://leetcode.com/problems/merge-two-sorted-lists/
## Iterative Method

```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
         ListNode dummy = new ListNode(0);
         ListNode current = dummy;
        while(list1 != null && list2 != null){
            if(list1.val < list2.val){
                current.next = list1;
                list1 = list1.next;
            }else {
                current.next = list2;
                list2 = list2.next;
            }

            current = current.next;
        }

        // If one list is longer than the other
        current.next = (list1 != null) ? list1 : list2;

        return dummy.next;
    }

}

```


## Recursive Method

```java
 class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if (list1 == null)
            return list2;
        if (list2 == null)
            return list1;

        if (list1.val > list2.val) {
            // Swap list1 and list2
            ListNode temp = list1;
            list1 = list2;
            list2 = temp;
        }

        list1.next = mergeTwoLists(list1.next, list2);
        return list1;
    }
}
```
