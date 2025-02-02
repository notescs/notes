```cpp
class Solution {
public:
    bool check(vector<int>& nums) {
        const bool isFirstHigher = nums.front() >= nums.back(); // there is a chance of rotation

        if (isFirstHigher) {
            int pivot = INT_MAX;
            for (int i = 1; i < (int)nums.size(); ++i) {
                if (nums[i] < nums[i - 1]) {
                    pivot = i + 1;
                    break;
                }
            }
            for (int i = pivot; i < (int)nums.size(); ++i) {
                if (nums[i] < nums[i - 1]) {
                    return false;
                }
                if (nums[i] > nums.front()) {
                    return false;
                }
            }
        } else {
            for (int i = 1; i < (int)nums.size(); ++i) {
                if (nums[i] < nums[i - 1]) {
                    return false;
                }
            }
        }

        return true;
    }
};
```
