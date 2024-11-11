# Examples
Input : arr [] = {1, 2, 5, 4, 3}
Output : Yes
By reversing the subarray {5, 4, 3}, the array will be sorted.


Input : arr [] = { 1, 2, 4, 5, 3 }
Output : No

```
 static boolean checkReverse(int arr[], int n) {
        // Copying the array
        int temp[] = new int[n];
        for (int i = 0; i < n; i++) {
            temp[i] = arr[i];
        }

        // Sort the copied array.
        Arrays.sort(temp);

        // Finding the first mismatch
        int front;
        for (front = 0; front < n; front++) {
            if (temp[front] != arr[front]) {
                break;
            }
        }

        // Finding the last mismatch
        int back;
        for (back = n - 1; back >= 0; back--) {
            if (temp[back] != arr[back]) {
                break;
            }
        }

        // If whole array is sorted
        if (front >= back) {
            return true;
        }

        // Checking if the subarray is decreasing or not using a for loop
        for (int i = front + 1; i <= back; i++) {
            if (arr[i - 1] < arr[i]) {  // If we find a pair that's not decreasing
                return false;
            }
        }

        return true;
    }
    
```