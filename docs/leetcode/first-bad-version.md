# First Bad Version

Question: [First Bad Version](https://leetcode.com/problems/first-bad-version/)

```java
class Solution {
    public int firstBadVersion(int n) {
    }
}
```

Linear Solution is trivial since it takes O(N) where N is given. Since it is "sorted", we should take advantage of Binary Search algorihtm.

## Binary Search

```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        if (n <= 0) return 0;
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (isBadVersion(mid)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}
```

*Time: O(log(N)) where N is given*  
*Space: O(1), in place*

Lucas  
Created: 03/19/2020
