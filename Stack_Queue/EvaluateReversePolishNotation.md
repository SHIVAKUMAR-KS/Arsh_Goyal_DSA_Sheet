
# Example
Example 1:

Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
Example 2:

Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
Example 3:

Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
 
 ```
 class Solution {
    public int evalRPN(String[] tokens) {
        int a,b;
        Stack<Integer> st=new Stack<Integer>();
        for(String str : tokens){
            if(str.equals("+")){
                st.add(st.pop()+st.pop());
            }else if(str.equals("/")){
                b=st.pop();
                a=st.pop();
                st.add(a/b);
            }else if(str.equals("*")){
                st.add(st.pop()*st.pop());
            }else if(str.equals("-")){
                b=st.pop();
                a=st.pop();
                st.add(a-b);
            }else{
                st.add(Integer.parseInt(str));
            }
        }
        return st.pop();
    }
}
```