
# Example
Example 1:

Input: s = "ab#c", t = "ad#c"
Output: true
Explanation: Both s and t become "ac".
Example 2:

Input: s = "ab##", t = "c#d#"
Output: true
Explanation: Both s and t become "".
Example 3:

Input: s = "a#c", t = "b"
Output: false
Explanation: s becomes "c" while t becomes "b".
 
----------------------------------------------------------------
 # Exaplanation 

In this question is asked for delete the one previous char from where '#' is came for example ab#c then it should be (ab) and (#c) should be deleted

and same things do for both string and check after performing the operation then compare the both string if it is same then return true otherwise return false

# Approach -1 (which is much  slower)
```
class Solution {
    public boolean backspaceCompare(String s, String t) {
        return solve(s).equals(solve(t));

    }
    public  String solve(String str) {
        Stack<Character> stack = new Stack<Character>();
        
        for (char c : str.toCharArray()) {
		
            if (c != '#') {
                stack.push(c);
				
            } else if (!stack.isEmpty()) {
                stack.pop();
            }
        }
        return stack.toString();
    }
}


```

