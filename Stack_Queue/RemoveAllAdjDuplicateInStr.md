# Examples
Example 1:

Input: s = "abbaca"
Output: "ca"
Explanation: 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".
Example 2:

Input: s = "azxxzy"
Output: "ay"
```
class Solution {
    public String removeDuplicates(String s) {
        StringBuilder sb=new StringBuilder();
        for(char ch: s.toCharArray()){
            int size=sb.length();
            if(size>0 && sb.charAt(size-1)==ch){
                sb.deleteCharAt(size-1);
            }else{
                sb.append(ch);
            }
        }
        return sb.toString();
    }
}
```