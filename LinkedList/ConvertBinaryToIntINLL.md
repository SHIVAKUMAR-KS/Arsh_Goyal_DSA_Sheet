# Examples
Example 1:


Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
Example 2:

Input: head = [0]
Output: 0
 
 ```
 class Solution {
    public int getDecimalValue(ListNode head) {
        String str="";
        while(head !=null){
            str=str+Integer.toString(head.val);
            head=head.next;
        }
        return Integer.parseInt(str,2);
    }
}
```