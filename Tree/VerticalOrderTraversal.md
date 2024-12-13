# Examples

![](https://assets.leetcode.com/uploads/2021/01/29/vtree1.jpg)

Input: root = [3,9,20,null,null,15,7]
--------
Output: [[9],[3,15],[20],[7]]
----------
Explanation:
Column -1: Only node 9 is in this column.
Column 0: Nodes 3 and 15 are in this column in that order from top to bottom.
Column 1: Only node 20 is in this column.
Column 2: Only node 7 is in this column.
```
class Pair {
    TreeNode node;
    int vertical;  // vertical position
    int depth;     // depth (level of traversal)
    Pair(TreeNode node, int vertical, int depth) {
        this.node = node;
        this.vertical = vertical;
        this.depth = depth;
    }
}

class Solution {
    public List<List<Integer>> verticalTraversal(TreeNode root) {
        List<List<Integer>> ans = new ArrayList<>();
        Queue<Pair> queue = new LinkedList<>();
        TreeMap<Integer, List<Pair>> map = new TreeMap<>();

        if (root == null) {
            return ans;
        }

        // Initialize the queue with the root node and its vertical position (0)
        queue.add(new Pair(root, 0, 0));  // vertical position 0, depth 0

        while (!queue.isEmpty()) {
            Pair pair = queue.poll();
            TreeNode node = pair.node;
            int vertical = pair.vertical;
            int depth = pair.depth;

            // Add the node and its depth to the corresponding list in the map
            map.putIfAbsent(vertical, new ArrayList<>());
            map.get(vertical).add(pair);

            // Add child nodes to the queue with updated vertical positions and depth
            if (node.left != null) {
                queue.add(new Pair(node.left, vertical - 1, depth + 1));
            }
            if (node.right != null) {
                queue.add(new Pair(node.right, vertical + 1, depth + 1));
            }
        }

        // Process the map to add nodes to the final answer
        for (List<Pair> value : map.values()) {
            // Sort by depth first, and by value if depths are equal
            value.sort((a, b) -> a.depth == b.depth ? a.node.val - b.node.val : a.depth - b.depth);
            
            List<Integer> verticalLevel = new ArrayList<>();
            for (Pair pair : value) {
                verticalLevel.add(pair.node.val);
            }
            ans.add(verticalLevel);
        }

        return ans;
    }
}
```