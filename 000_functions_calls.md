## Understanding Function Calls 
In Python, functions can call other functions to break down a problem into smaller, manageable tasks. This improves **code readability, reusability, and maintainability**.  

### Using Missing Number as an Example 

In our **Missing Number** example, we define a helper function, `add_all()`, which calculates the sum of a list. Then, we call `add_all()` inside `missing_number()` to compute the actual sum of the given numbers.  

---

### Example Code  

```python
def add_all(nums):
    """
    This function sums all the elements in the given nums.
    """
    total = 0
    for num in nums:
        total += num
    return total

def missing_number(nums: list[int]) -> int:
    """
    Finds the missing number in the range [0, n] from the given list of n distinct numbers.
    """
    n = len(nums)
    expected_total = int((0 + n) * (n + 1) / 2)
    actual_total = add_all(nums)
    return expected_total - actual_total

# Test Cases
assert missing_number([0, 1, 3]) == 2
assert missing_number([0, 1, 2, 3]) == 4
assert missing_number([0]) == 1

print("All test cases passed!")
```

---

### Explanation of Function Calls  

1. **Defining `add_all()`**  
   - This function iterates through the given list and sums all the elements.  
   - Instead of using Python’s built-in `sum()`, we use `add_all()` for educational purposes.  

2. **Calling `add_all()` Inside `missing_number()`**  
   - Instead of `sum(nums)`, we use `add_all(nums)` to get the sum of the given numbers.  
   - `missing_number()` doesn’t need to know how `add_all()` works internally—it just **calls** it and **uses** the result.  

---

### Why Use a Separate Function?  
- **Code Reusability**: `add_all()` can be used anywhere else in the program.  
- **Readability**: `missing_number()` stays focused on solving the missing number problem.  
- **Modularity**: If we need to modify how we sum elements (e.g., handling special cases), we only change `add_all()`, not every place where we sum numbers.  

---

### Key Takeaway  
📌 **In Python, a function can call another function by simply using its name followed by parentheses `function_name(arguments)`.**  

For example, in `missing_number(nums)`, we call `add_all(nums)`, and it returns the sum, which we then use to compute the missing number.
