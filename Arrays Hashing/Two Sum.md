# Two Sum

### Question?
* Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

**Example 1:**

> Input: nums = [2,7,11,15], target = 9
>
> Output: [0,1]
>
> Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

> Input: nums = [3,2,4], target = 6
>
> Output: [1,2]

**Example 3:**

> Input: nums = [3,3], target = 6
>
> Output: [0,1]
 

**Constraints:**

* 2 <= nums.length <= 104
* -109 <= nums[i] <= 109

### Answer

Thought Process:

* We need to find two numbers in the array that add up to the target sum.
* We can use a hash table to store array elements and their indices.
* For every element, we check if target - element exists in hash table.
* If yes, we have found the two numbers that sum to target.
* We return their indices.

cpp
```cpp
vector<int> twoSum(vector<int>& nums, int target) {
  unordered_map<int, int> map; 

  for(int i = 0; i < nums.size(); i++) {
    int complement = target - nums[i];
    if(map.find(complement) != map.end()) {
      return {map[complement], i}; 
    }
    map[nums[i]] = i;
  }
  
  return {};
}
```

python
```python3
def twoSum(nums, target):
  numMap = {}
  
  for i, n in enumerate(nums):
    complement = target - n
    if complement in numMap:
      return [numMap[complement], i]
    numMap[n] = i
    
  return []
```

Key steps:

* Use hash table to store array elements and indices
* Check if complement exists in table
* Return indices if found

  
