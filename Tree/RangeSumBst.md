# Examples
Example 1:


Input: root = [10,5,15,3,7,null,18], low = 7, high = 15
Output: 32
Explanation: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.
Example 2:


Input: root = [10,5,15,3,7,13,18,1,null,6], low = 6, high = 10
Output: 23
Explanation: Nodes 6, 7, and 10 are in the range [6, 10]. 6 + 7 + 10 = 23.

```
class Solution {
    public int rangeSumBST(TreeNode root, int low, int high) {

        if(root==null){
            return 0;
        }
        int sum=root.val>=low && root.val<=high ? root.val:0;

        if(root.left !=null){
            sum +=rangeSumBST(root.left,low,high);
        }
        if(root.right !=null){
            sum +=rangeSumBST(root.right,low,high);
        }
        return sum;
        
    }
}

```