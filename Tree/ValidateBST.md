# Example

![](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

Input: root = [2,1,3]

Output: true

----------------------------------------------------------------
![](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

Input: root = [5,1,4,null,null,3,6]
Output: 
false

Explanation: The root node's value is 5 but its right child's value is 4.

```
class Solution {
    public boolean isValidBST(TreeNode root) {
        
        return valid(root,null,null);
    }
    public boolean valid(TreeNode root,TreeNode min,TreeNode max){
        if(root==null){
            return true;
        }
        if(min !=null && root.val<=min.val){
            return false;
        }
        if(max !=null && root.val>=max.val){
            return false;
        }
        return valid(root.left,min,root) && valid(root.right,root,max);
    }
}
```
