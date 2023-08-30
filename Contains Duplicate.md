# Contains Duplicated
### Question?
* Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

**Example 1:**

> Input: nums = [1,2,3,1]

> Output: true

**Example 2:**

> Input: nums = [1,2,3,4]

> Output: false

**Example 3:**

> Input: nums = [1,1,1,3,3,4,3,2,4,2]

> Output: true
 

**Constraints:**

* ```1 <= nums.length <= 105```
* ```-109 <= nums[i] <= 109```

### Answer
Thought Process:

* The problem requires us to check if there are any duplicate elements in the given integer array.
* A simple approach is to put all elements in a hash table/map and check if any element maps to more than one value.
* In C++, we can use an unordered_map to store each element and its count.
* In Python, we can use a dictionary for the same purpose.
* We iterate through the array, and for each element, we check if it already exists in the map/dict.
* If yes, we increment its count.
* Finally we check if any element has a count more than 1. If yes, return true. Else return false.

**cpp**
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int, int> freq;

        for (int n: nums) {
            freq[n]++;
            if(freq[n]>1) {
                return true;
            }
        }
        return false;
    }
};
```
**python**
```python3
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        freq = {}
        
        for n in nums:
            if n in freq:
                freq[n] += 1
                if freq[n] > 1:
                    return True
            else:
                freq[n] = 1
                
        return False
```

The key steps are:

* Use a hash table/map to store frequency of each element
* Iterate through the array and increment count if element already seen
* Check if any element has count > 1, if yes return true
* If no element has count > 1, return false

