# Example
Example 1:

Input: s = "0"

Output: true

Example 2:

Input: s = "e"

Output: false

Example 3:

Input: s = "."

Output: false

 

Constraints:

1 <= s.length <= 20
s consists of only English letters (both uppercase and lowercase), digits (0-9), plus '+', minus '-', or dot '.'.



```
class Solution {
    public boolean isNumber(String s) {
        if(s==null || s.isEmpty()){
            return false;
        }
        boolean seenDigit =false;
        boolean seenDot =false;
        boolean seenE =false;

        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);

            if(Character.isDigit(ch)){
                seenDigit =true;
            }else if(ch=='+' || ch=='-'){
                if(i>0 && s.charAt(i-1)!='e' && s.charAt(i-1)!='E'){
                    return false;
                }
            }else if(ch=='.'){
                if(seenDot || seenE){
                    return false;
                }
                seenDot=true;
            }else if(ch=='e'||ch=='E'){
                if(!seenDigit || seenE){
                    return false;
                }
                seenE =true;
                seenDigit=false;
            }else{
                return false;
            }
        }
        return seenDigit;
    }
}
```
