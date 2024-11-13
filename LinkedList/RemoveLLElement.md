# Example
Example 1:


Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
Example 2:

Input: head = [], val = 1
Output: []
Example 3:

Input: head = [7,7,7,7], val = 7
Output: []

```
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head==null){
            return null;
        }

        ListNode dummy=new ListNode();
        dummy.next=head;
        ListNode temp=dummy;

        while(temp.next!=null){
            if(temp.next.val==val){
                temp.next=temp.next.next;
            }else{
                temp=temp.next;
            }
        }
        return dummy.next;
     

        
    }
}
```