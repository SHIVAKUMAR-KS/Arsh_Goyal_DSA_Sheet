### Example 1:

Input: 
haystack = "sadbutsad", 
needle = "sad"
Output: 0
----------------------------------------------------------------
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.

### Example 2:

Input: haystack = "leetcode", needle = "leeto"
Output: -1
----------------------------------------------------------------
Explanation: "leeto" did not occur in "leetcode", so we return -1.


 ### to solve the problem
 1.using indexOf property we can solve this 
 #
 2.indexOf property will basically return index if it find the given string into main string
 #
 ```

 class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.isEmpty()) return 0;
        return haystack.indexOf(needle);
    }
}
 ```