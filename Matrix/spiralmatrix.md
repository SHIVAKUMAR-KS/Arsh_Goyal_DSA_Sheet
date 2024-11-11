# Examples

Example 1:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
Example 2:

```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> res=new ArrayList<>();

        int n=matrix.length;
        int m=matrix[0].length;
        int startRow=0;
        int endRow=n-1;
        int startCol=0;
        int endCol=m-1;

        while(startRow<=endRow && startCol<=endCol){
            //first row
            for(int j=startCol;j<=endCol;j++){
                res.add(matrix[startRow][j]);
            }
            startRow +=1;
            //end row
            for(int i=startRow;i<=endRow;i++){
                res.add(matrix[i][endCol]);
            }
            endCol -=1;

            //----
            if(startRow<=endRow){

                //end row
                for(int j=endCol;j>=startCol;j--){
                    res.add(matrix[endRow][j]);
                }
                endRow -=1;
            }
            if(startCol <=endCol){

                //first row
                for(int i=endRow;i>=startRow;i--){
                    res.add(matrix[i][startCol]);
                }
                startCol +=1;
            }

        }
        return res;
        
    }
}
```

