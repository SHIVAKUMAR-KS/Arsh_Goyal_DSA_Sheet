# Examples
Input: arr[] = [10, 3, 5, 6, 2]
Output: [180, 600, 360, 300, 900]
Explanation: For i=0, pro[i] = 3*5*6*2 = 180.
For i=1, pro[i] = 10*5*6*2 = 600.
For i=2, pro[i] = 10*3*6*2 = 360.
For i=3, pro[i] = 10*3*5*2 = 300.
For i=4, pro[i] = 10*3*5*6 = 900.

```
 int n = nums.length;
        
        // Initialize the right product array
        long[] right = new long[n];
        long[] result = new long[n];
        
        // Initialize product variables
        long pro = 1;
        
        // Calculate the product of elements to the right of each index
        for (int i = n - 1; i >= 0; i--) {
            right[i] = pro;
            pro *= nums[i]; // Update the cumulative product from the right
        }
        
        // Initialize left product variable
        long left = 1;
        
        // Now combine the left and right products
        for (int i = 0; i < n; i++) {
            result[i] = left * right[i];
            left *= nums[i]; // Update the cumulative product from the left
        }
        
        return result;
```