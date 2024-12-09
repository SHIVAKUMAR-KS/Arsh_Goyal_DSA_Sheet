# Examples


![BST Example](https://assets.leetcode.com/uploads/2021/02/05/bst1.jpg)

Input: root = [4,2,6,1,3]
Output: 1

![Example 2](https://assets.leetcode.com/uploads/2021/02/05/bst2.jpg)

Input: root = [1,0,48,null,null,12,49]
Output: 1

```
class Solution {

    int min=Integer.MAX_VALUE;
    Integer prev=null;
    public int getMinimumDifference(TreeNode root) {
        
        if(root==null){
            return min;
        }
        getMinimumDifference(root.left);

        if(prev!=null){
            min=Math.min(min,root.val-prev);
        }
        prev=root.val;
        getMinimumDifference(root.right);
        return min;
    }
}

```

# This problem is exalty similar with this
```
783. Minimum Distance Between BST Nodes```