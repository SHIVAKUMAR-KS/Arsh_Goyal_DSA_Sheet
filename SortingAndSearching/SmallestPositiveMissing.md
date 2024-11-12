# Examples
Input: arr[] = [2, -3, 4, 1, 1, 7]
Output: 3
Explanation: Smallest positive missing number is 3.
Input: arr[] = [5, 3, 2, 5, 1]
Output: 4
Explanation: Smallest positive missing number is 4.
```
Arrays.sort(arr);
        int count=1;
        
        for(int i=0;i<arr.length;i++){
            if(arr[i]==count){
                count++;
            }
        }
        return count;
```
```
class Solution {
    // Function to find the smallest positive number missing from the array.
    public int missingNumber(int[] arr) {
        // Your code here
          int n = arr.length;
        
        // Step 1: Clean the array to only focus on numbers in the range [1, n].
        for (int i = 0; i < n; i++) {
            if (arr[i] <= 0 || arr[i] > n) {
                arr[i] = n + 1;  // Replace irrelevant numbers with a large number out of range
            }
        }

        // Step 2: Use array indexing to mark numbers
        for (int i = 0; i < n; i++) {
            int num = Math.abs(arr[i]);
            if (num <= n) {
                // Mark the index corresponding to the number as visited (negative marking)
                if (arr[num - 1] > 0) {
                    arr[num - 1] = -arr[num - 1];
                }
            }
        }

        // Step 3: Identify the smallest missing positive number
        for (int i = 0; i < n; i++) {
            if (arr[i] > 0) {
                return i + 1;  // The smallest missing number is i + 1
            }
        }

        // Step 4: If all numbers from 1 to n are present, return n + 1
        return n + 1;
    }
}

```