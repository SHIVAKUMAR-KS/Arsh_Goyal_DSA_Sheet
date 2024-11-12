# Example
Example 1:


Input: head = [1,1,2]
Output: [1,2]
Example 2:


Input: head = [1,1,2,3,3]
Output: [1,2,3]

```
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode list=head;

        while(list !=null){
            if(list.next==null){
                break;
            }
            if(list.val==list.next.val){
                list.next=list.next.next;
            }else{
                list=list.next;
            }
        }
        return head;
    }
}
```