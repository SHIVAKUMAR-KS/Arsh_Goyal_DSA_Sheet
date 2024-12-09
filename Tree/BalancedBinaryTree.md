
# Example

![](https://assets.leetcode.com/uploads/2020/10/06/balance_1.jpg)

Input: root = [3,9,20,null,null,15,7]

Output: true

----------------------------------------------------------------
![](https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg)

Input: root = [1,2,2,3,3,null,null,4,4]

Output: false

----------------------------------------------------------------
Example 3:

Input: root = []

Output: true
 ```
 class Solution {
    public boolean isBalanced(TreeNode root) {
        if(root==null){
            return true;
        }
        return height(root)!=-1;
    }
    public int height(TreeNode root){
        if(root==null){
            return 0;
        }
        int left=height(root.left);
        int right=height(root.right);
        int balanceFactor=Math.abs(left-right);

        if(balanceFactor>1 || left ==-1 || right==-1){
            return -1;
        }
        return 1+Math.max(left,right);
    }
}

```