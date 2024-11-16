# Examples
Input: S = "231*+9-"
Output: -4
Explanation:
After solving the given expression, 
we have -4 as result.


# Dry run of the above example
"231*+9-"
->3*1=3(23+9-)
->2+3=5(59-)
->5-9=-4  that is the answer

```
class Solution
{
    //Function to evaluate a postfix expression.
    public static int evaluatePostFix(String S)
    {
        // Your code here
        Stack<Integer> st=new Stack<>();
        
        int n=S.length();
        for(int i=0;i<n;i++){
            char ch=S.charAt(i);
            
            if(Character.isDigit(ch)){
                st.push(ch-'0');
            }else{
                int val1=st.pop();
                int val2=st.pop();
                
                switch(ch){
                    case '+':
                        st.push(val1+val2);
                        break;
                    case '-':
                        st.push(val2-val1);
                        break;
                    case '*':
                        st.push(val1*val2);
                        break;
                    case '/':
                        st.push(val2/val1);
                        break;
                }
            }
            
        }
        return st.pop(); //return the last element which will be kept finally that is our finall anser
        
    }
}
```
