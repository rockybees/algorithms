## Problem Statement:
**[LeetCode27](https://leetcode.com/problems/remove-element/) - Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` in-place. The order of the elements may be changed. Then return the number of elements in `nums` which are not equal to `val`.**

**Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:**

**Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of nums.
Return `k`.**


### Step 1: Understand the Problem (Using Examples)
**We can understand the problem by walking through some examples:**

1. **Example 1:**
   ```plaintext
   Input: nums = [3,2,2,3], val = 3
   Output: 2, nums = [2,2,_,_]
   Explanation: Your function should return k = 2, with the first two elements of nums being 2. It does not matter what you leave beyond the returned k (hence they are underscores).
   ```

2. **Example 2:**
   ```plaintext
   Input: nums = [0,1,2,2,3,0,4,2], val = 2
   Output: 5, nums = [0,1,4,0,3,_,_,_]
   Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
   Note that the five elements can be returned in any order. It does not matter what you leave beyond the returned k (hence they are underscores).
   ```


---

### Step 2: Develop an Algorithm (Using Pseudocode or Flowchart)

#### Algorithm:
1. Initialize `k = 0` to track the position for the next non-val element.
2. Loop through nums, copying non-val elements to `nums[k]` and increasing `k`.
3. Return `k` as the new length.

---

### Step 3: Translate the Algorithm into Code
```python
def remove_element(nums: list[int], val: int) -> int:
    """
    This function removes all occurrences of val in nums in-place.
    """
    k = 0 # k tracks where to place the next non-val element
    for num in nums:
        if num != val:
            nums[k] = num
            k += 1
    return k

# Test Cases
assert remove_element([0, 1, 3], 3) == 2
assert remove_element([0, 1, 2, 2, 3], 2) == 3
assert remove_element([0, 3], 2) == 2

print("All test cases passed!")
```

### Other Methods: 
#### Algorithm 2

```python
def remove_element(nums: list[int], val: int) -> int:
    """
    This function removes all occurrences of val in nums in-place.
    """
    nums_length = len(nums)
    index_left = 0
    index_right = nums_length - 1
    while index_left <= index_right:
        if nums[index_left] == val:
            # Swap two elements using tuple unpacking
            nums[index_left], nums[index_right] = nums[index_right], val
            index_right -= 1
        else:
            index_left += 1
    return index_left
```
