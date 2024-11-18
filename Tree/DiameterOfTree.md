# Example
Example 1:


Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
Example 2:

Input: root = [1,2]
Output: 1

```
class Solution {
     int maxDiameter = 0;

    public int dfs(TreeNode node) {
        if(node == null) return 0;

        int leftDepth = dfs(node.left);
        int rightDepth = dfs(node.right);
        maxDiameter = Math.max(maxDiameter, leftDepth + rightDepth);

        return Math.max(leftDepth , rightDepth) + 1;
    }

    public int diameterOfBinaryTree(TreeNode root) {
        
        dfs(root);
        return maxDiameter;
    }
}
```