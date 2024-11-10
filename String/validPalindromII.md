# Examples
Example 1:

Input: s = "aba"
Output: true
Example 2:

Input: s = "abca"
Output: true
Explanation: You could delete the character 'c'.
Example 3:

Input: s = "abc"
Output: false

```
class Solution {
    public boolean isPalindrome(String s,int start,int end){
        while(start<end){
            if(s.charAt(start) !=s.charAt(end)){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
    public boolean validPalindrome(String s) {
        int n=s.length();
        int start=0;
        int end=n-1;

        while(start<end){
            if(s.charAt(start)!=s.charAt(end)){
                return isPalindrome(s,start+1,end) || isPalindrome(s,start,end-1);
            }
            start++;
            end--;
        }
        return true;

       
    }
}
```