# Two Sum

Question: [Two Sum](https://leetcode.com/problems/two-sum/)

The [official Solution](https://leetcode.com/problems/two-sum/solution/) from Leetcode is really decent. This question is really informative actually. It provides a sort of "thinking framework" on solving algorithm interview questions.

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
    }
}
```

Note: Ask the input, output types during the actual interview. Do not assume it is the exact question on Leetcode.

## Brute Force Solution

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if (nums == null && nums.length == 0) return new int[0];
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            for (int j = i+1; j < n; j++) {
                if (nums[i] + nums[j] == target) return new int[]{i, j};
            }
        }
        return new int[]{-1, -1};
    }
}
```

*Time: O(N * N) where N is the length of nums*\n
*Space: O(1), in-place solution.*

Now, thinking about why this solution is inefficient?
Normally, we can think of sorting since it is O(NlogN) than O(N * N). However given we need to return the index, we'd better
not to change the index, which is required when using sorting algorithm.

Another common technique is to trade space for a better time complexity. A classic data structure is HashTable (Dictionary).

## Two Pass HashMap

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if (nums == null && nums.length == 0) return new int[0];
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], i);
        }
        for (int i = 0; i < nums.length; i++) {
            int comp = target - nums[i];
            if (map.containsKey(comp)  && map.get(comp) != i) {
                return new int[] {i, map.get(comp)};
            }
        }
        return new int[]{-1, -1};
    }
}
```

*Time: O(N) where N is the length of nums*\n
*Space: O(N) The extra space is determined by the number of items stored in the hash table, which stores exactly N items*

Again, how to improve it?
We only need to have one HashMap to save space.

## One Pass HashMap

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        if (nums == null && nums.length == 0) return new int[0];
        Map<Integer, Integer> maps = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int current = nums[i];
            if (maps.containsKey(target-current)) {
                return new int[]{maps.get(target-current), i};
            }
            maps.put(current, i);
        }
        return new int[]{-1, -1};
    }
}
```

*Time: O(N)*\n
*Space: O(N) The extra space is determined by the number of items stored in the hash table, which stores at most N items*

Lucas Xu\n
03/18/2020
