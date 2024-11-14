# Example
Example 1:


Input: l1 = [7,2,4,3], l2 = [5,6,4]
Output: [7,8,0,7]
Example 2:

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [8,0,7]
Example 3:

Input: l1 = [0], l2 = [0]
Output: [0]
 


```
class Solution {
    public ListNode helper(ListNode l1,ListNode l2){
        Stack<Integer> stack1=new Stack<>();
        Stack<Integer> stack2=new Stack<>();

        while(l1 !=null){
            stack1.push(l1.val);
            l1=l1.next;
        }

        while(l2 !=null){
            stack2.push(l2.val);
            l2=l2.next;
        }

        ListNode res=null;
        int carry=0;

        while(!stack1.isEmpty() || !stack2.isEmpty() || carry!=0){
            int digit1=!stack1.isEmpty() ? stack1.pop():0;
            int digit2=!stack2.isEmpty() ? stack2.pop():0;

            int sum=digit1+digit2+carry;
            int digit=sum%10;
            carry=sum/10;

            ListNode newNode=new ListNode(digit);
            newNode.next=res;
            res=newNode;
        }
        return res;
    }
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        
        ListNode ans=helper(l1,l2);
        return ans;
    }
}
```