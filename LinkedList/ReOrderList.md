# Examples
    Example 1:


Input: head = [1,2,3,4]
Output: [1,4,2,3]
Example 2:


Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
 


```
class Solution {
    // Reverse the second half of the list
    public ListNode reverse(ListNode head) {
        ListNode current = head;
        ListNode prev = null;

        while (current != null) {
            ListNode nextNode = current.next;
            current.next = prev;
            prev = current;
            current = nextNode;
        }

        return prev;
    }

    // Merge two lists in alternating fashion
    public void merge(ListNode l1, ListNode l2) {
        while (l1 != null && l2 != null) {
            ListNode n1 = l1.next;
            ListNode n2 = l2.next;

            l1.next = l2;
            if (n1 == null) break;  // If no more nodes in l1, we’re done
            l2.next = n1;

            l1 = n1;
            l2 = n2;
        }
    }

    public void reorderList(ListNode head) {
        if (head == null || head.next == null) {
            return; // No reordering needed for empty or single node list
        }

        ListNode prev = null;
        ListNode slow = head;
        ListNode fast = head;

        // Find the middle of the list using the slow and fast pointers
        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        // Split the list into two halves
        prev.next = null;  // End the first half
        ListNode l1 = head;
        ListNode l2 = slow;

        // Step 2: Reverse the second half of the list
        l2 = reverse(l2);

        // Step 3: Merge the two halves
        merge(l1, l2);
    }
}

```