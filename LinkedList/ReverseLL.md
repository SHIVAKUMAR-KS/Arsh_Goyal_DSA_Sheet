
# Example
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
Example 2:


Input: head = [1,2]
Output: [2,1]
Example 3:

Input: head = []
Output: []

```
class Solution {
    public ListNode reverseList(ListNode head) {

        ListNode current=head;
        ListNode prev=null;

        while(current !=null){
            ListNode newNode=current.next;
            current.next=prev;
            prev=current;
            current =newNode;
        }
        
    return prev;
    }
}
```