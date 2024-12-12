# Example

Example 1:

Input: root = [1,null,2,3]
![](https://assets.leetcode.com/uploads/2024/08/29/screenshot-2024-08-29-202743.png)
Output: [1,3,2]

--------------------------------
Example 2:

Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]
![](https://assets.leetcode.com/uploads/2024/08/29/tree_2.png)
Output: [4,2,6,5,7,1,3,9,8]

```
class Solution {
    public void inorderTraversalHelper(TreeNode root,List<Integer> res){

        if(root==null){
            return;
        }

        inorderTraversalHelper(root.left,res);
        res.add(root.val);
        inorderTraversalHelper(root.right,res);
    }
    public List<Integer> inorderTraversal(TreeNode root) {
        ArrayList<Integer> res=new ArrayList<>();
        inorderTraversalHelper(root,res);
        return res;
    }

}
```