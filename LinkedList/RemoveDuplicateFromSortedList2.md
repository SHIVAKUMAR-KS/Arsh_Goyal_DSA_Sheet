# Examples

IN this question ,which element is repreatable delete it completely with duplicates also
Example 1:


Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]
Example 2:


Input: head = [1,1,1,2,3]
Output: [2,3]

```
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        if(head.val!=head.next.val){
            head.next=deleteDuplicates(head.next);
            return head;
        }

        while(head.next!=null && head.val==head.next.val){
            head=head.next;
        }
        return deleteDuplicates(head.next);
    }
}
```