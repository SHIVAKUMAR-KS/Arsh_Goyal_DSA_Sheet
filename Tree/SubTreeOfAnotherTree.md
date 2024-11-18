
# Example
Example 1:


Input: root = [3,4,5,1,2], subRoot = [4,1,2]
Output: true
Example 2:


Input: root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]
Output: false
 

 ```
 class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        
        if(root==null){
            return false;
        }
        if(helper(root,subRoot)){
            return true;
        }
        return isSubtree(root.left,subRoot) || isSubtree(root.right,subRoot);
    }
    public boolean helper(TreeNode root,TreeNode subRoot){
        if(root==null && subRoot==null){
            return true;
        }
        if(root==null || subRoot==null){
            return false;
        }

        if(root.val !=subRoot.val){
            return false;
        }
        return helper(root.left,subRoot.left)&&helper(root.right,subRoot.right);
    }
}
```