# Example
Example 1:

Input: num = "1432219", k = 3

Output: "1219"

Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
----------------------------------------------------------------
Example 2:

Input: num = "10200", k = 1

Output: "200"

Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.
Example 3:
--------------------------------
Input: num = "10", k = 2

Output: "0"

Explanation: Remove all the digits from the number and it is left with nothing which is 0.
 
 ```
 class Solution {
    public String removeKdigits(String num, int k) {
        int n=num.length();
        if(n==k){
            return "0";
        }
        Stack<Character> st=new Stack<>();
        int i=0;

        while(i<n){
            //which is less than the previous digit,discard it
            while(k>0 && !st.isEmpty() && st.peek()>num.charAt(i)){
                st.pop();
                k--;
            }
            st.push(num.charAt(i));
            i++;
        }
        //case like 1111
        while(k>0){
            st.pop();
            k--;
        }

        StringBuilder res =new StringBuilder();
        while(!st.isEmpty()){
            res.append(st.pop());
        }
        res.reverse();
        //remove all the 0 at the head;
        while(res.length()>1 && res.charAt(0)=='0'){
            res.deleteCharAt(0);
        }
        return res.toString();
    }
}
```