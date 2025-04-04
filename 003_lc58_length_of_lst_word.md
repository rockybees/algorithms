## Problem Statement:
**Given a string s consisting of words and spaces, return the length of the last word in the string. A word is a maximal substring consisting of non-space characters only.**


### Step 1: Understand the Problem (Using Examples)
**We can understand the problem by walking through some examples:**

1. **Example 1:**
   ```plaintext
   Input: s = "Hello World"
   Output: 5
   Explanation: The last word is "World" with length 5.
   ```

2. **Example 2:**
   ```plaintext
   Input: s = "   fly me   to   the moon  "
   Output: 4
   Explanation: The last word is "moon" with length 4.
   ```

3. **Example 3:**
   ```plaintext
   Input: s = "luffy is still joyboy"
   Output: 6
   Explanation: The last word is "joyboy" with length 6.
   ```

---

### Step 2: Develop an Algorithm (Using Pseudocode or Flowchart)

#### Algorithm:
1. Initialize `i` as the last index of `s`.
2. Use a while loop to skip spaces from the end.
3. Count the last word as long as `i >= 0` and `s[i]` is a non-space.
4. Return the count.

---

### Step 3: Translate the Algorithm into Code
```python
def lengthOfLastWord(s: str) -> int:
    i = len(s) - 1
    length_last_word = 0
    while s[i] == ' ':
        i = i - 1
    while i >= 0 and s[i] != ' ':
        length_last_word += 1
        i -= 1
    return length_last_word

assert lengthOfLastWord('   fly me   to   the moon  ') == 4
assert lengthOfLastWord('luffy is still joyboy') == 6
assert lengthOfLastWord('Hello World') == 5

print("All test cases passed!")
```

### Other Methods: 
#### Algorithm 2 using s.split()
```python
def lengthOfLastWord(s: str) -> int:
    return len(s.split()[-1])
```
