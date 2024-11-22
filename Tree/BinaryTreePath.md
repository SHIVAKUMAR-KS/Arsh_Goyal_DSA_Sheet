# Examples
Example 1:


Input: root = [1,2,3,null,5]
Output: ["1->2->5","1->3"]
Example 2:

Input: root = [1]
Output: ["1"]

```
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> res=new ArrayList<>();
        if(root!=null){
            searchBT(root,"",res);

        }
        return res;
    }
    public void searchBT(TreeNode root,String path,List<String> res){
        if(root.left==null && root.right==null){
            res.add(path+root.val);
        }
        if(root.left !=null){
            searchBT(root.left,path+root.val+"->",res);
        }
        if(root.right !=null){
            searchBT(root.right,path+root.val+"->",res);
        }
    }
}
```