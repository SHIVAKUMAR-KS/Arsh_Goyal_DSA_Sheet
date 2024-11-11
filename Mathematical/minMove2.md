# Example
Example 1:

Input: nums = [1,2,3]
Output: 2
Explanation:
Only two moves are needed (remember each move increments or decrements one element):
[1,2,3]  =>  [2,2,3]  =>  [2,2,2]
Example 2:

Input: nums = [1,10,2,9]
Output: 16
 
 ```
 class Solution {
    public int minMoves2(int[] nums) {
        Arrays.sort(nums);
        int i=0;
        int j=nums.length-1;
        int count=0;

        while(i<j){
            count+=nums[j]-nums[i];
            i++;
            j--;
        }
        return count;
    }
}
 ```