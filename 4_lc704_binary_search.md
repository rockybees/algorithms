## Problem Statement:
**[LeetCode704](https://leetcode.com/problems/binary-search/description/) - Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.
You must write an algorithm with O(log n) runtime complexity.**


### Step 1: Understand the Problem (Using Examples)


**We can understand the problem by walking through some examples:**

1. **Example 1:**
   ```plaintext
   Input: nums = [-1,0,3,5,9,12], target = 9
   Output: 4
   Explanation: 9 exists in nums and its index is 4
   Output: 2
   ```

2. **Example 2:**
   ```plaintext
   Input: nums = [-1,0,3,5,9,12], target = 2
   Output: -1
   Explanation: 2 does not exist in nums so return -1
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
The search range becomes empty, return -1 indicating the target is not found.
```    

---

### Step 3: Translate the Algorithm into Code
c
```c
#include <stdio.h>

int binary_search(int nums[], int size, int target) {
    int low = 0;
    int high = size - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (nums[mid] < target)
            low = mid + 1;
        else if (nums[mid] > target)
            high = mid - 1;
        else 
            return mid;
    }
    return -1;
}

int main() {
    int nums[] = {2, 3, 5, 9};
    int index = binary_search(nums, 4, 10);
    printf("The target's index is: %d\n", index);
}
```
python
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low = 0
        high = len(nums) - 1
        while low <= high:
            mid = (low + high) // 2
            if nums[mid] > target:
                high = mid - 1 
            elif nums[mid] < target:
                low = mid + 1 
            else:
                return mid
        return -1
```

### Other Methods: 
#### Algorithm 1.1 - high is 1-index higher than the searching range
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        low = 0
        high = len(nums)
        while low < high:
            mid = (low + high) // 2
            if (nums[mid] < target):
                low = mid + 1
            elif (nums[mid] > target):
                high = mid
            else:
                return mid
        return -1
```

#### Algorithm 2 - recursive
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        def helper(self, low: int, high: int) -> int:
            if low > high:
                return -1
            mid = floor((low + high) /2)
            if nums[mid] == target:
                return mid
            elif nums[mid] > target:
                return helper(self, low, mid - 1)
            else:
                return helper(self, mid + 1, high)
            
        low = 0
        high = len(nums) - 1
        return helper(self, low, high)
```
