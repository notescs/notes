```cpp
class Solution {
public:
    long long countBadPairs(vector<int>& nums) {
        // i < j and j - i != nums[i] - nums[j]
        // j - nums[j] = i - nums[i] --> need to group these

        const int n = nums.size();

        long long goodPairs = 0;
    
        unordered_map<int, int> diffFreq;

        for (int i = 0; i < n; ++i) {
            const int diff = i - nums[i];
            goodPairs += static_cast<long long>(diffFreq[diff]);
            ++diffFreq[diff];
        }

        return static_cast<long long>(n) * (n - 1) / 2 - goodPairs;
    }
};
```
