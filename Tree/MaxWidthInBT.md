# Examples

![](https://assets.leetcode.com/uploads/2021/05/03/width1-tree.jpg)

Input: root = [1,3,2,5,3,null,9]

Output: 4

Explanation: The maximum width exists in the third level with length 4 (5,3,null,9)

----------------------------------------------------------------
![](https://assets.leetcode.com/uploads/2022/03/14/maximum-width-of-binary-tree-v3.jpg)

Input: root = [1,3,2,5,null,null,9,6,null,7]

Output: 7

Explanation: The maximum width exists in the fourth level with length 7 (6,null,null,null,null,null,7).




```
class Solution {
    public int widthOfBinaryTree(TreeNode root) {
         if (root == null) {
            return 0;
        }

        Queue<Pair<TreeNode, Long>> queue = new LinkedList<>();
        queue.offer(new Pair<>(root, 0L)); // Root node with position 0
        long maxWidth = 0;

        while (!queue.isEmpty()) {
            int size = queue.size();
            long first = queue.peek().getValue();
            long last = first;

            // Traverse all nodes at the current level
            for (int i = 0; i < size; i++) {
                Pair<TreeNode, Long> pair = queue.poll();
                TreeNode curr = pair.getKey();
                long position = pair.getValue();

                // Update the last position
                last = position;

                if (curr.left != null) {
                    queue.offer(new Pair<>(curr.left, 2 * position + 1));
                }
                if (curr.right != null) {
                    queue.offer(new Pair<>(curr.right, 2 * position + 2));
                }
            }

            // Calculate the width of the current level
            maxWidth = Math.max(maxWidth, last - first + 1);
        }

        return (int) maxWidth;
        
    }
}
```