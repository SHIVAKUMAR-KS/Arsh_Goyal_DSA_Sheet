
# Example
Example 1::

Input: p = [1,2,3], q = [1,2,3]
Output: true
Example 2:


Input: p = [1,2], q = [1,null,2]
Output: false
Example 3:


Input: p = [1,2,1], q = [1,1,2]
Output: false
```
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {

        if(p==null && q==null){
            return true;
        }
        if(p==null || q==null){
            return false;
        }

        return (p.val==q.val)&& isSameTree(p.left,q.left)&& isSameTree(p.right,q.right);
        
    }
}
```