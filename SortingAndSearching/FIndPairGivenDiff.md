# Given
Given an array, arr[] and an integer x, return true if there exists a pair of elements in the array whose absolute difference is x, otherwise, return false.

Examples:

Input: arr[] = [5, 20, 3, 2, 5, 80], x = 78
Output: true
Explanation: Pair (2, 80) have an absolute difference of 78.
Input: arr[] = [90, 70, 20, 80, 50], x = 45
Output: false
Explanation: There is no pair with absolute difference of 45.
Input: arr[] = [1], x = 1
Output: false

```
class Solution {
    public boolean findPair(int[] arr, int x) {
        // code here
        int n=arr.length;
        Arrays.sort(arr);
        int start=0;
        int end=1;
        while(end<n && start<n){
            if(arr[end]-arr[start]==x && start!=end){
                return true;
            }else if(arr[end]-arr[start]<x){
                end++;
            }else{
                start++;
            }
        }
        return false;
    }
}

```