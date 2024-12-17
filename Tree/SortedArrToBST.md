# Example

![](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)

Input: nums = [-10,-3,0,5,9]

Output: [0,-3,9,-10,null,5]

Explanation: [0,-10,5,null,-3,null,9] is also accepted:


--------------------------------
![](https://assets.leetcode.com/uploads/2021/02/18/btree.jpg)
Input: nums = [1,3]

Output: [3,1]

Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
 
 ```
 class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums.length==0){
            return null;
        }

        return helper(nums,0,nums.length-1);
    }
    public TreeNode helper(int nums[],int low,int high){
        if(low>high){
            return null;
        }
        int mid=(low+high)/2;
        TreeNode node=new TreeNode(nums[mid]);
        node.left=helper(nums,low,mid-1);
        node.right=helper(nums,mid+1,high);

        return node;
    }

}