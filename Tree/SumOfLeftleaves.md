

# Example
![](https://assets.leetcode.com/uploads/2021/04/08/leftsum-tree.jpg)

Input: root = [3,9,20,null,null,15,7]
Output: 24
Explanation: There are two left leaves in the binary tree, with values 9 and 15 respectively.

--------------------------------
Example 2:

Input: root = [1]
Output: 0
 ```
 class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        
        //for better
        if(root==null){
            return 0;
        }
        return getSum(root,false);
    }
    public int getSum(TreeNode root,boolean isLeftChild){
        if(root.left==null && root.right==null){
            return (isLeftChild)?root.val:0;
        }
        int sum=0;
        if(root.left!=null){
            sum+=getSum(root.left,true);
        }
        if(root.right!=null){
            sum+=getSum(root.right,false);
        }
        return sum;
    }
}
```