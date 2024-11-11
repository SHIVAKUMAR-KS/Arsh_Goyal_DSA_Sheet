# Examples
Example 1:

Input: nums = [1,2,3]
Output: 3
Explanation: Only three moves are needed (remember each move increments two elements):
[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
Example 2:

Input: nums = [1,1,1]
Output: 0
 
 

 ```class Solution {
    public int minMoves(int[] nums) {
        int min=Integer.MAX_VALUE;
        int sum=0;

        for(int num:nums){
            min=Math.min(min,num);
            sum+=num;
        }
        return sum-min*nums.length;
        
    }
}
```