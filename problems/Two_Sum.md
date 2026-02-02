**Problem Description:**
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.



**Example 1:**
Input: nums = \[2,7,11,15], target = 9

Output: \[0,1]

Explanation: Because nums\[0] + nums\[1] == 9, we return \[0, 1].



**Example 2:**



Input: nums = \[3,2,4], target = 6

Output: \[1,2]

**Approaches:**

**Brute Force:**
use two for loops + traverse + Find target + i!=j + return indexes 
We use two nested loops to traverse the array.
The outer loop selects the first element, and the inner loop selects the second element.
For every pair of indices (i, j), we check whether:

i != j (to avoid using the same element twice)

nums[i] + nums[j] == target

If both conditions are satisfied, we immediately return the indices i and j as the answer.

This approach ensures that all possible pairs are checked, so it always finds the correct solution if one exists.

**Complexity**

Time Complexity: O(n²) — due to two nested loops

Space Complexity: O(1) — no extra data structures used

  public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[] { i, j };
                }
            }
        }
    return new int[] {};
  }

**optimal:**

Traverse the array once while storing each number with its index in a HashMap.
For every element, compute target - currentValue.
If this complement already exists in the map, return the stored index and the current index.
Otherwise, store the current value and its index in the map.
This achieves a single-pass solution with linear time complexity.

Time Complexity: O(n)
Space Complexity: O(n)
public int[] twoSum(int[] nums, int target) {
            HashMap<Integer, Integer> map = new HashMap<>();
            for (int i = 0; i < nums.length; i++) {
                int complement = target - nums[i];
                if (map.containsKey(complement)) {
                    return new int[] { map.get(complement), i };
                }
                map.put(nums[i], i);
            }
   return new int[] {};
}





