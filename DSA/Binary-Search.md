# Binary Search Templates

## Template 1

```cpp
int binarySearch(vector<int>& nums, int target){
  if(nums.size() == 0)
    return -1;

  int left = 0, right = nums.size() - 1;
  while(left <= right){
    // Prevent (left + right) overflow
    int mid = left + (right - left) / 2;
    if(nums[mid] == target){ return mid; }
    else if(nums[mid] < target) { left = mid + 1; }
    else { right = mid - 1; }
  }

  // End Condition: left > right
  return -1;
}
```

## Sqrt(x)

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        start = 0
        end = x
        ans = 0
        while end >= start:
            mid = (start + end) // 2
            cur = mid * mid
            if cur == x:
                return mid
            elif cur > x:
                end = mid - 1
            else:
                ans = mid
                start = mid + 1
        return ans
```
