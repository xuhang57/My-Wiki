# Search a 2D Matrix

Question: [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
    }
}
```

## Binary Search

Given the matrix is sorted. We can use a modified binary search to find the target efficiently.

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0) return false;
        int m = matrix.length, n = matrix[0].length;
        int range = m * n;
        int left = 0, right = range - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            int r = mid / n;
            int c = mid % n;
            if (matrix[r][c] == target) return true;
            else if (matrix[r][c] > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return false;
    }
}
```

*Time: O(log(MN)) where M and N are the dimensions of the matrix*  
*Space: O(1), in place*

Lucas  
Created: 03/20/2020
