# Examples
Example 1:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
Example 2:


Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
 
 ```
 class Solution {
    public void rotate(int[][] matrix) {
        int n=matrix.length;

        //step 1: transpose the matrix
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[j][i];
                matrix[j][i] =temp;
            }
        }
        //step 2 :Reverse the matrix
        for(int i=0;i<n;i++){
            for(int j=0;j<n/2;j++){
                int temp =matrix[i][j];
                matrix[i][j]=matrix[i][n-1-j];
                matrix[i][n-1-j]=temp;
            }
        }
    }
}
```