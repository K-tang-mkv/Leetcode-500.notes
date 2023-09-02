# Group Anagrams

### Question?
* Given an array of strings strs, group the anagrams together. You can return the answer in any order.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

> Input: strs = ["eat","tea","tan","ate","nat","bat"]
>
> Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

**Example 2:**

> Input: strs = [""]
>
> Output: [[""]]

**Example 3:**

> Input: strs = ["a"]
>
> Output: [["a"]]
 

**Constraints:**

* 1 <= strs.length <= 104
* 0 <= strs[i].length <= 100
* strs[i] consists of lowercase English letters.

### Answer
Thought Process:

* Anagrams are strings that contain same characters in different order.
* We need to group strings that are anagrams together.
* We can use a hash map to store string as key and list of anagrams as value.
* For each string, calculate a key that is the sorted string.
* Store the string in hash map's list using the calculated key.
> * Strings that are anagrams will have the same key, so will go to same list.

cpp
```cpp
vector<vector<string>> groupAnagrams(vector<string>& strs) {
  unordered_map<string, vector<string>> map;

  for(auto str : strs) {
    string key = str;
    sort(key.begin(), key.end());
    map[key].push_back(str); 
  }

  vector<vector<string>> result;
  for(auto it : map) {
    result.push_back(it.second);
  }

  return result;
}
```

python
```python3
from collections import defaultdict

def groupAnagrams(strs):
  map = defaultdict(list)
  
  for s in strs:
    sorted_s = ''.join(sorted(s))
    map[sorted_s].append(s)

  return map.values()
```

Key points:

* Use hashmap to store sorted string as key
* Store original string in map's list
* Strings with same key are grouped as anagrams

  
