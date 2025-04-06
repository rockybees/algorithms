## Problem Statement:
**Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.**


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
def two_sum(nums: list[int], target: int) -> list[int]:
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return []

# Test Cases
assert two_sum([3, 3], 6) == [0, 1]
assert two_sum([3, 2, 4], 6) == [1, 2]
assert two_sum([2,7,11,15], 9) == [0, 1]

print("All test cases passed!")
```

### Other Methods: 
#### Algorithm 2 using s.split()
```python
def lengthOfLastWord(s: str) -> int:
    return len(s.split()[-1])
```







# Approach 1 BruteForce 
```
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;
        int n = nums.size();
        for (int i = 0; i < n - 1; i++)
            for (int j = i + 1; j < n; j++)
                if (nums[i] + nums[j] == target)
                    return {i, j};
        return {};
    } // T: O(n^2) S: O(1)
```

# Approach 2 Hashmap (Best here)
```
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        unordered_map<int, int> m;
        for (int i = 0; i < n; i++)
            if (m.count(target - nums[i])) 
                return {m[target - nums[i]], i};
            else m.insert({nums[i], i}); // Or m[nums[i]] = i; fine since assume one solution.
        return {};
    } // Best T: O(n) S: O(n) // Classic example of using space to save time. Approach 1 - > Approach 2.
```

# Amazon OA [Find Pair with Given Sum](https://leetcode.com/discuss/interview-question/356960)
```
    vector<int> twoSumBiggest(vector<int>& nums, int tar) {
        int n = nums.size();
        vector<int> res;
        map<int, vector<int>> m;
        for (int i = 0; i < n - 1; i++)
            for (int j = i + 1; j < n; j++)
                if (nums[i] + nums[j] == tar - 30)
                    m.insert({max(nums[i], nums[j]), {i, j}});
        if (m.size() > 0) return m.rbegin()->second;
        return {};
    } // F1 BruteForce + map(BST) T: O(n^2klgk) S:O(k)
```
```
   vector<int> twoSumBiggest(vector<int>& nums, int tar) {
        int n = nums.size();
        unordered_map<int, int> m;
        unordered_map<int, vector<int>> unmap;
        for (int i = 0; i < n; i++) {
            int comp = tar - 30 - nums[i];
            if (m.count(comp))
                unmap.insert({max(nums[i], comp), {m[comp], i}});
            else m.insert({nums[i], i});
        }
        if (unmap.size() == 0) return {};
        vector<int> res;
        int max_key = INT_MIN;
        for (auto& mm: unmap)
            max_key = max(max_key, mm.first);
        for (auto& mm: unmap)
            if (mm.first == max_key)
                return mm.second;
        return res;
    } // F2 hashmap Good T: O(n + k) S:O(n + k)
```
```
    vector<int> twoSumBiggest(vector<int>& nums, int tar) {
        int n = nums.size();
        unordered_map<int, int> m;
        int max_key = INT_MIN;
        vector<int> res;
        for (int i = 0; i < n; i++) {
            int comp = tar - 30 - nums[i];
            if (m.count(comp)) {
                if (nums[i] > max_key || comp > max_key) {
                    res = {m[comp], i};
                    max_key = max(nums[i], comp);
                }
            }
            else m.insert({nums[i], i});
        }
        return res;
    } // F2.1 hashmap Best!!! T: O(n) S: O(n)
```
Driver's function:
```
        vector<int> ns = {1, 10, 25, 35, 60};
        //vector<int> ns = {20, 50, 40, 25, 30, 10};
        int tar = 90;
        //vector<int> ns = {0, 0};
        //int tar = 30;
        vector<int> res = twoSumBiggest(ns, tar);
        for (auto& e: res)
            cout<< e<< " ";
```

# Amazon OA [two sum - unique pairs](https://leetcode.com/discuss/interview-question/372434)
```
    int twoSumUnique(vector<int>& ns, int tar) {
        int n = ns.size();
        unordered_set<int> s;
        unordered_set<int> res;
        for (int i = 0; i < n; i++)
            if (s.count(tar - ns[i]))
                res.insert(min(tar - ns[i], ns[i]));
            else s.insert(ns[i]);
        return res.size();
    }
```

