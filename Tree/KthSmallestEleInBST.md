# Example
![](https://assets.leetcode.com/uploads/2021/01/28/kthtree1.jpg)

Input: root = [3,1,4,null,2], k = 1

Output: 1
---------
![](https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg)

Input: root = [5,3,6,2,4,null,null,1], k = 3

Output: 3
```
class Solution {
    int ans=Integer.MAX_VALUE;
    int count=1;
    public int kthSmallest(TreeNode root, int k) {
        if(root==null){
            return 0;
        }
        kthSmallest(root.left,k);
        if(count==k){
            ans=root.val;
        }
        count++;
        kthSmallest(root.right,k);
        return ans;
    }
}
```