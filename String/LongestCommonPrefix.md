###  Longest Common Prefix

# Example
Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
         if (strs == null || strs.length == 0) {
        return "";
    }
    
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix.isEmpty()) {
                return "";
            }
        }
    }
    
    return prefix;
    }
}
```

# Explanation
