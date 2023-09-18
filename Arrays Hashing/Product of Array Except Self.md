# Product of Array Except Self
### Question?
* Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
You must write an algorithm that runs in O(n) time and without using the division operation.

**Example 1:**

> Input: nums = [1,2,3,4]
>
> Output: [24,12,8,6]

**Example 2:**

> Input: nums = [-1,1,0,-3,3]
>
> Output: [0,0,9,0,0]
 

**Constraints:**

* 2 <= nums.length <= 105
* -30 <= nums[i] <= 30
* The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

### Answer

Thought process:

* We need to find product of all elements except the element at each index.
* We can calculate left and right products separately.
* Left product will store product of all left elements.
* Right product will store product of all right elements.
* To avoid division, we can calculate left products from left to right.
* And calculate right products from right to left.
* Finally answer[i] = left[i] * right[i] will be product except self.

CPP
```cpp
vector<int> productExceptSelf(vector<int>& nums) {
  
  int n = nums.size();
  vector<int> left(n, 1);
  vector<int> right(n, 1);

  for(int i=1; i<n; i++) {
    left[i] = left[i-1] * nums[i-1]; 
  }
  
  for(int i=n-2; i>=0; i--) {  
    right[i] = right[i+1] * nums[i+1];
  }

  vector<int> ans(n, 1);
  for(int i=0; i<n; i++) {
    ans[i] = left[i] * right[i]; 
  }

  return ans;
}
```

Python
```python3
def productExceptSelf(nums):
  
  n = len(nums)
  left = [1] * n
  right = [1] * n

  left[0] = 1
  for i in range(1, n):
    left[i] = left[i-1] * nums[i-1]

  right[n-1] = 1  
  for i in range(n-2, -1, -1):
    right[i] = right[i+1] * nums[i+1]

  output = [left[i] * right[i] for i in range(n)]

  return output
```

