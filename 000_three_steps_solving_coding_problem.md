# 3 Steps to Solve a Coding Problem: "Missing Number" Example

## Problem Statement:
**Given a list of numbers containing `n` distinct integers in the range `[0, n]`, return the only number in the range that is missing from the list.**


### Step 1: Understand the Problem (Using Examples)


**Examples:**

1. **Example 1:**
   ```plaintext
   Input: [0, 1, 3]
   n = 3 (since there are 3 numbers in the list, the range is [0, 1, 2, 3])
   Expected range: [0, 1, 2, 3]
   Missing number: 2
   Output: 2
   ```

2. **Example 2:**
   ```plaintext
   Input: [0, 1, 2, 3]
   n = 4 (the range should be [0, 1, 2, 3, 4])
   Expected range: [0, 1, 2, 3, 4]
   Missing number: 4
   Output: 4
   ```

3. **Example 3:**
   ```plaintext
   Input: [0]
   n = 1 (the range should be [0, 1])
   Expected range: [0, 1]
   Missing number: 1
   Output: 1
   ```

---

### Step 2: Develop an Algorithm (Using Pseudocode or Flowchart)

One efficient approach to solve this problem is by using the arithmetic series sum formula. The sum of the first `n` natural numbers is given by:

`S_n = (0 + n) * (n + 1) / 2`

#### Algorithm (a set of steps):
1. Compute the sum of numbers in the full expected range using the formula: `expected_sum = n * (n + 1) / 2`
2. Compute the sum of the given list: `actual_sum`
3. The missing number is the difference: `missing_number = expected_sum - actual_sum`

---

### Step 3: Translate the Algorithm into Code

Although the algorithm is given, try to implement it by yourself first before looking at the code below!

```python
def missing_number(nums: list[int]) -> int:
    n = len(nums)
    expected_total = int((0 + n) * (n + 1) / 2)
    actual_total = 0
    for num in nums:
        actual_total += num
    return expected_total - actual_total

# Test Cases
assert missing_number([0, 1, 3]) == 2
assert missing_number([0, 1, 2, 3]) == 4
assert missing_number([0]) == 1

print("All test cases passed!")
```

This method runs in **O(n) time complexity** and **O(1) space complexity**, making it very efficient.

