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

```python
def lengthOfLastWord(s: str) -> int:
    return len(s.split()[-1])
```
