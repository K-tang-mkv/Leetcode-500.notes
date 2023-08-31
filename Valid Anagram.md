# Valid Anagram
### Question
* Given two strings s and t, return true if t is an anagram of s, and false otherwise.
An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**

> Input: s = "anagram", t = "nagaram"
> 
> Output: true

**Example 2:**

> Input: s = "rat", t = "car"
>
> Output: false
 

**Constraints:**

* 1 <= s.length, t.length <= 5 * 104
* s and t consist of lowercase English letters.

### Answer

Thought Process:

* Anagrams are strings that contain the same characters but in different order.
* So we need to check if both strings contain the same characters with same frequency.
* We can count the frequency of characters in each string and compare the resulting maps.
* In C++, we can use a map<char, int> to store frequency of chars.
* In Python, we can use a dictionary for this purpose.
* We iterate through s and increment count for each char.
* Similarly we iterate through t and decrement count of chars.
* Finally if all counts are 0, the two strings are anagrams.

**cpp**
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        map<char, int> freq;
        
        for(char c : s) {
            freq[c]++; 
        }
        
        for(char c : t) {
            freq[c]--;
        }
        
        for(auto it : freq) {
            if(it.second != 0) {
                return false;
            }
        }
        return true;
    }
};
```
**python**
```python3
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        freq = {}
        
        for ch in s:
            freq[ch] = freq.get(ch, 0) + 1
            
        for ch in t:
            freq[ch] = freq.get(ch, 0) - 1
            
        for count in freq.values():
            if count != 0:
                return False
            
        return True
```
The key steps are:

* Use map/dict to store char frequencies
* Increment count for chars in s
* Decrement count for chars in t
* If all counts are 0, s and t are anagrams
