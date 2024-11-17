# Examples
# We have to determine what is the earliest time after which all the oranges are rotten. A rotten orange at index [i, j] can rot other fresh orange at indexes [i-1, j], [i+1, j], [i, j-1], [i,j+1] (up, down, left and right) in unit time.
Input: mat = [[0, 1, 2], [0, 1, 2], [2, 1, 1]]
Output: 1
Explanation: The mat is-
0 1 2
0 1 2
2 1 1
Oranges at positions (0,2), (1,2), (2,0) will rot oranges at (0,1), (1,1), (2,2) and (2,1) in unit time.
Input: mat = [[2, 2, 0, 1]]
Output: -1
Explanation: The mat is - 2 2 0 1
Oranges at (0,0) and (0,1) can't rot orange at (0,3).
Input: mat = [[2, 2, 2], [0, 2, 0]]
Output: 0
Explanation: The mat is - 
2 2 2
0 2 0
There is no fresh orange.

```


class Solution {
    // Function to find minimum time required to rot all oranges.
    public int orangesRotting(int[][] mat) {
        int row = mat.length;
        int col = mat[0].length;
        
        Queue<int[]> queue = new LinkedList<>();
        int freshOrange = 0;
        
        // Step 1: Add all rotten oranges to the queue and count fresh oranges
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                if (mat[i][j] == 2) {
                    queue.add(new int[]{i, j}); // Rotten orange position
                } else if (mat[i][j] == 1) {
                    freshOrange++; // Count fresh oranges
                }
            }
        }
        
        // If there are no fresh oranges, return 0 immediately
        if (freshOrange == 0) {
            return 0;
        }
        
        int min = 0;
        int dirs[][] = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}}; // Directions: up, down, left, right
        
        // Step 2: Perform BFS from all rotten oranges
        while (!queue.isEmpty()) {
            int size = queue.size();
            boolean rotOrange = false;
            
            for (int i = 0; i < size; i++) {
                int[] cur = queue.poll();
                for (int[] dir : dirs) {
                    int newX = cur[0] + dir[0];
                    int newY = cur[1] + dir[1];
                    
                    // If the neighboring cell is within bounds and contains a fresh orange
                    if (newX >= 0 && newX < row && newY >= 0 && newY < col && mat[newX][newY] == 1) {
                        mat[newX][newY] = 2; // Rot the fresh orange
                        queue.add(new int[]{newX, newY});
                        freshOrange--; // Decrease count of fresh oranges
                        rotOrange = true;
                    }
                }
            }
            
            // If any fresh orange was rotted, increment the time
            if (rotOrange) {
                min++;
            }
        }
        
        // If all fresh oranges have rotted, return the time, else return -1
        return freshOrange == 0 ? min : -1;
    }
}
```