
# Example
Example 1:

Input: citations = [0,1,3,5,6]

Output: 3

Explanation: [0,1,3,5,6] means the researcher has 5 papers in total and each of them had received 0, 1, 3, 5, 6 citations respectively.
Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, their h-index is 3.
Example 2:
------------------------------------------------
Input: citations = [1,2,100]

Output: 2
```
class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);
        int index=0;
        int n=citations.length;
        for(int i=0;i<n;i++){
            if(citations[(n-1)-i]>=i+1){
                index=i+1;
            }
        }
        return index;
    }
}
```