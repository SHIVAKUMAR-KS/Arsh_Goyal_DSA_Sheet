# Examples
Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: 3
Example 2:

Input: root = [1,null,2]
Output: 2

```
class Solution {
    public int maxDepth(TreeNode root) {

        if(root==null){
            return 0;
        }
        int lh=maxDepth(root.left);
        int rh=maxDepth(root.right);
        
        return 1+Math.max(lh,rh);
    }
}

```