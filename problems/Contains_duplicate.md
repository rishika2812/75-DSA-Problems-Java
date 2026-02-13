## **Problem Description:**

Given an integer array **nums**, return **true** if any value appears at least twice in the array, and return **false** if every element is distinct.

## Solutions:

### Approach 1:

Compare every element with every other element.

If any pair is equal, return true.

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        for(int i = 0; i < nums.length; i++) {
            for(int j = i + 1; j < nums.length; j++) {
                if(nums[i] == nums[j]) {
                    return true;
                }
            }
        }
        return false;
    }
}
```

TC: O(n^2)

SC: O(1)

### Approach 2:

Sort the array and check adjacent elements.

```java
import java.util.Arrays;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        
        for(int i = 1; i < nums.length; i++) {
            if(nums[i] == nums[i - 1]) {
                return true;
            }
        }
        
        return false;
    }
}
```

TC: O(nlogn)

SC: O(1)

### Approach 3:

Using a HashSet to track seen elements.

For every number:

- If already in set, duplicate found
- Else, add to set

or by just comparing the size of set with size of array.

```java
import java.util.HashSet;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        
        for(int num : nums) {
            if(set.contains(num)) {
                return true;
            }
            set.add(num);
        }
        
        return false;
    }
}
```

TC: O(n)

SC: O(n)