# Examples
Example 1:

Input: columnNumber = 1
Output: "A"
Example 2:

Input: columnNumber = 28
Output: "AB"
Example 3:

Input: columnNumber = 701
Output: "ZY"

```
class Solution {
    public String convertToTitle(int columnNumber) {


        StringBuilder sb=new StringBuilder();

        while(columnNumber>0){
            columnNumber--;

            int remainder=columnNumber%26;
            char ch =(char) ('A'+remainder);
            sb.insert(0,ch);
            columnNumber /=26;
        }
        return sb.toString();
        
    }
}
```