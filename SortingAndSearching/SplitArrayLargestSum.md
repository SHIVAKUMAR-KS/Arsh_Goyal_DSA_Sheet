# Hard Level Question
# Examples
Example 1:

Input: nums = [7,2,5,10,8], k = 2
Output: 18
Explanation: There are four ways to split nums into two subarrays.
The best way is to split it into [7,2,5] and [10,8], where the largest sum among the two subarrays is only 18.
Example 2:

Input: nums = [1,2,3,4,5], k = 2
Output: 9
Explanation: There are four ways to split nums into two subarrays.
The best way is to split it into [1,2,3] and [4,5], where the largest sum among the two subarrays is only 9.
 

```
class Solution {
    public int splitArray(int[] nums, int k) {
        int low = Integer.MIN_VALUE, high = 0;

        for(int num : nums){
            low = Math.max(low, num);
            high += num;
        }

        while(low<=high){
            int mid = low + (high - low)/2;
            int counts = noOfSubArray(nums, mid);

            if(counts<=k) high = mid - 1;
            else {
                low = mid + 1;
            }
        }
        return low;
    }
    public static int noOfSubArray(int nums[],int sumMax){
       int count = 1, sum = 0;

        for(int x : nums){
            if(x+sum <=sumMax){
                sum += x;
            }
            else {
                count++;
                sum = x;
            }
        }
        return count;
    }
}
```