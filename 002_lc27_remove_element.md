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
