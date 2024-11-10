# Examples
Example 1:

Input: path = "/home/"

Output: "/home"

Explanation:

The trailing slash should be removed.

Example 2:

Input: path = "/home//foo/"

Output: "/home/foo"

Explanation:

Multiple consecutive slashes are replaced by a single one.

Example 3:

Input: path = "/home/user/Documents/../Pictures"

Output: "/home/user/Pictures"

Explanation:

A double period ".." refers to the directory up a level (the parent directory).

Example 4:

Input: path = "/../"

Output: "/"

Explanation:

Going one level up from the root directory is not possible.

### Steps
1.create a stack

```
class Solution {
    public String simplifyPath(String path) {
        Stack<String> st=new Stack<>();

        String components[]=path.split("/");

        for(String component:components){
            if(component.equals("") || component.equals(".")){
                continue;
            }

            if(component.equals("..")){
                if(!st.isEmpty()){
                    st.pop();
                }
            }else{
                st.push(component);
            }
        }

        if(st.isEmpty()){
            return "/";
        }

        StringBuilder res=new StringBuilder();
        for(String dir : st){
            res.append("/").append(dir);
        }
        return res.toString();
    }
}
```