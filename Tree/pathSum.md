
# Examples
 Example 1:

![](https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg)

Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1],
 targetSum = 22


Output: true

Explanation: The root-to-leaf path with the target sum is shown.
Example 2:

--------------------------------

![](https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg)

Input: root = [1,2,3], targetSum = 5


Output: false
Explanation: There are two root-to-leaf paths in the tree:
(1 --> 2): The sum is 3.
(1 --> 3): The sum is 4.
There is no root-to-leaf path with sum = 5.
Example 3:

Input: root = [], targetSum = 0
Output: false
Explanation: Since the tree is empty, there are no root-to-leaf paths.
 
----------------------------------------------------------------
Constraints:

The number of nodes in the tree is in the range [0, 5000].
-1000 <= Node.val <= 1000
-1000 <= targetSum <= 1000

```
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        if(root==null){
            return false;
        }
        if(root.left ==null  && root.right==null && targetSum-root.val==0){
            return true;
        }
        return hasPathSum(root.left,targetSum-root.val) || hasPathSum(root.right,targetSum-root.val);
    }
}
```