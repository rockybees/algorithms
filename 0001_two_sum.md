## Problem Statement:
**Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.**


### Step 1: Understand the Problem (Using Examples)
**We can understand the problem by walking through some examples:**

1. **Example 1:**
   ```plaintext
   Input: nums = [2,7,11,15], target = 9
   Output: [0,1]
   Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
   ```

2. **Example 2:**
   ```plaintext
   Input: nums = [3,2,4], target = 6
   Output: [1,2]
   ```

3. **Example 3:**
   ```plaintext
   Input: nums = [3,3], target = 6
   Output: [0,1]
   ```

---

### Step 2: Develop an Algorithm (Using Pseudocode or Flowchart)

#### Algorithm - Brute force solution:
1. Loop through all pairs of numbers using nested for-loops.
2. If a pair sums to the target, return their indices.
3. Return an empty list if no valid pair is found.

---

### Step 3: Translate the Algorithm into Code
```python
def two_sum(nums: list[int], target: int) -> list[int]:
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return []
# Time complexity: O(n^2)
# Space complexity: O(1)

# Test Cases
assert two_sum([3, 3], 6) == [0, 1]
assert two_sum([3, 2, 4], 6) == [1, 2]
assert two_sum([2,7,11,15], 9) == [0, 1]

print("All test cases passed!")
```

### Other Methods: 
#### Algorithm 2 - Using space (dictionary/hashmap) to save time (Classic Example)
```python
def two_sum(nums: list[int], target: int) -> list[int]:
    num_to_index = {}
    for i in range(len(nums)):
        if target - nums[i] in num_to_index:
            return [num_to_index[target - nums[i]], i]
        else:
            num_to_index[nums[i]] = i
    return []

# Time complexity: O(n)
# Space complexity: O(n)
```

