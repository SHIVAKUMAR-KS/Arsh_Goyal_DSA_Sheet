# Examples
Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []
 
 ```
 class Solution {
    public ListNode mergeKLists(ListNode[] lists) {

        if(lists.length==0 || lists==null){
            return null;
        }
        ListNode head=new ListNode(0);
        ListNode temp=head;

        ArrayList<Integer> res=new ArrayList<>();
        for(ListNode list : lists){
            while(list !=null){
                res.add(list.val);
                list=list.next;
            }
        }
        Collections.sort(res);
        for(int value: res){
            temp.next=new ListNode(value);
            temp=temp.next;
        }
        return head.next;
    }
}
```