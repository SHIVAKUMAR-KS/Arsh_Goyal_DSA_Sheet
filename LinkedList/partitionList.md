
# Example
Example 1:


Input: head = [1,4,3,2,5,2], x = 3
Output: [1,2,2,4,3,5]
Example 2:

Input: head = [2,1], x = 2
Output: [1,2]
----------------------------------------------------------------
The idea is to use two pointers (or references) to create two separate linked lists:

One for nodes with values less than x
Another for nodes with values greater than or equal to x
At the end, we can combine the two linked lists to get the desired result.
----------------------------------------------------------------
```
class Solution {
    public ListNode partition(ListNode head, int x) {
        
        ListNode before=new ListNode(0);
        ListNode after=new ListNode(0);
        ListNode before_curr=before;
        ListNode after_curr=after;

        while(head !=null){
            if(head.val<x){
                before_curr.next=head;
                before_curr=before_curr.next;
            }else{
                after_curr.next=head;
                after_curr=after_curr.next;
            }
            head=head.next;
        }
        after_curr.next=null;
        before_curr.next=after.next;

        return before.next;
        
    }
}
```