```
class Solution
{
     static void countingSort(int nums[], int n, int exp) {
        int[] output = new int[n];
        int[] count = new int[10];

        // Store count of occurrences of (nums[i] / exp) % 10
        for (int i = 0; i < n; i++) {
            count[(nums[i] / exp) % 10]++;
        }

        // Change count[i] so that count[i] now contains the actual position of this digit in output[]
        for (int i = 1; i < 10; i++) {
            count[i] += count[i - 1];
        }

        // Build the output array
        for (int i = n - 1; i >= 0; i--) {
            output[count[(nums[i] / exp) % 10] - 1] = nums[i];
            count[(nums[i] / exp) % 10]--;
        }

        // Copy the output array to nums[], so that nums[] now contains sorted numbers
        System.arraycopy(output, 0, nums, 0, n);
    }
    static void radixSort(int nums[], int n) 
    { 
        // code here 
         int max = nums[0];
        for (int i = 1; i < n; i++) {
            if (nums[i] > max) {
                max = nums[i];
            }
        }

        // Do counting sort for every digit. Note that the exp (exponent) is 10^i.
        for (int exp = 1; max / exp > 0; exp *= 10) {
            countingSort(nums, n, exp);
        }
    } 
}

```