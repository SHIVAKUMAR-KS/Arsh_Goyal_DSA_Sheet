# Examples

![](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

Input: root = [3,9,20,null,null,15,7]

Output: [[3],[9,20],[15,7]]

----------------------------------------------------------------
Example 2:

Input: root = [1]
Output: [[1]]
Example 3:

Input: root = []
Output: []

```
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res=new ArrayList<>();
        if(root==null){
            return res;

        }
        Queue<TreeNode> queue=new LinkedList<>();
        queue.add(root);

        while(!queue.isEmpty()){
            int size=queue.size();
            ArrayList<Integer> levelAns=new ArrayList<>();
            for(int i=0;i<size;i++){
                TreeNode node=queue.poll();
                levelAns.add(node.val);

                if(node.left !=null){
                    queue.add(node.left);
                }

                if(node.right !=null){
                    queue.add(node.right);
                }
            }
            res.add(levelAns);
        }
        return res;
    }
}
```