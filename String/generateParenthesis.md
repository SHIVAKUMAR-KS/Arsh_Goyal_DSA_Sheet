# Example
Example 1:

Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
Example 2:

Input: n = 1
Output: ["()"]

```
class Solution {
    public void solve(int n,List<String> list,StringBuilder sb,int co,int cc){
        if(sb.length() ==2*n){
            list.add(sb.toString());
            return;

        }
        if(co<n){
            sb.append("(");
            solve(n,list,sb,co+1,cc+1);
            sb.deleteCharAt(sb.length()-1);
        }
        if(cc>0){
            sb.append(")");
            solve(n,list,sb,co,cc-1);
            sb.deleteCharAt(sb.length()-1);
        }
    }
    public List<String> generateParenthesis(int n) {
        List<String> list=new ArrayList<>();
        solve(n,list,new StringBuilder(),0,0);
        return list;
    }
}
```