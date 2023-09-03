# Top K Frequent Elements
### Question?
* Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

 

**Example 1:**

> Input: nums = [1,1,1,2,2,3], k = 2
>
> Output: [1,2]

**Example 2:**

> Input: nums = [1], k = 1
>
> Output: [1]
 

**Constraints:**

* 1 <= nums.length <= 105
* -104 <= nums[i] <= 104
* k is in the range [1, the number of unique elements in the array].
* It is guaranteed that the answer is unique.

### Answer

Thought Process:

* We need to find frequencies of all elements in the array.
* We can use a hash map to store the element as key and its frequency as value.
* Then we traverse this hash map and maintain a min heap of size k.
* The min heap will contain the k most frequent elements seen so far.
* Finally we return the elements in the min heap as result.

C++ Solution:
```cpp
vector<int> topKFrequent(vector<int>& nums, int k) {
  unordered_map<int, int> freq;
  for(int n : nums) {
    freq[n]++;
  }
  
  priority_queue<pair<int, int>, vector<pair<int,int>>, greater<pair<int,int>>> pq;
  
  for(auto it : freq) {
    pq.push({it.second, it.first});
    if(pq.size() > k) {
      pq.pop();
    }
  }
  
  vector<int> result;
  while(!pq.empty()) {
    result.push_back(pq.top().second);
    pq.pop();
  }
  return result;
}
```

Python Solution:
```python3
import heapq
from collections import Counter

def topKFrequent(nums, k):
  freq = Counter(nums)
  
  pq = []
  for n, c in freq.items():
    heapq.heappush(pq, (-c, n))
    if len(pq) > k:
      heapq.heappop(pq)
      
  result = []
  while pq:
    result.append(heapq.heappop(pq)[1])
  
  return result
```

