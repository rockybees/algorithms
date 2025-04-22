## Problem Statement:
**[LeetCode744](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/) - You are given an array of characters `letters` that is sorted in non-decreasing order, and a character `target`. There are at least two different characters in `letters`.
Return the smallest character in `letters` that is lexicographically greater than `target`. If such a character does not exist, return the first character in `letters`.**

### Step 1: Understand the Problem (Using Examples)


**We can understand the problem by walking through some examples:**

1. **Example 1:**
   ```plaintext
   Input: letters = ["c","f","j"], target = "a"
   Output: "c"
   Explanation: The smallest character that is lexicographically greater than 'a' in letters is 'c'.
   ```

2. **Example 2:**
   ```plaintext
   Input: letters = ["c","f","j"], target = "c"
   Output: "f"
   Explanation: The smallest character that is lexicographically greater than 'c' in letters is 'f'.
   ```

3. **Example 3:**
   ```plaintext
   Input: letters = ["x","x","y","y"], target = "z"
   Output: "x"
   Explanation: There are no characters in letters that is lexicographically greater than 'z' so we return letters[0].
   ```

---

### Step 2: Develop an Algorithm (Using Pseudocode or Flowchart)

#### Algorithm:
```
Start searching the entire array using lowest and highest indices.
Repeat the following steps until the search range is empty:
    Find the middle position of the current search range.
    If the middle value is less than the target value:
        Narrow the search range to the higher half.
    Else if the middle value is greater than the target value:
        Narrow the search range to the lower half.
    Else (the middle value equals the target):
        Find the target and return its index.
The search range becomes empty
If the low index crosses highest or the high index crosses lowest:
    return the first character indicating the target is not found.
Else:
    letters[low] is the smallest one greater than target, return it.
```    

---

### Step 3: Translate the Algorithm into Code
```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        lo = 0
        hi = len(letters) - 1
        while lo <= hi:
            mid = (lo + hi) // 2
            if (letters[mid] <= target):
                lo = mid + 1
            elif (letters[mid] > target):
                hi = mid - 1
        if lo == len(letters) or hi == -1:
            return letters[0]
        else:
            return letters[lo]
```

### Other Methods: 
#### Algorithm 1.1 - high is 1-index higher than the searching range
```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        lo = 0
        hi = len(letters)
        while lo < hi:
            mid = (lo + hi) // 2
            if (letters[mid] <= target):
                lo = mid + 1
            elif (letters[mid] > target):
                hi = mid
        if lo != len(letters):
            return letters[lo]
        else:
            return letters[0]
```
