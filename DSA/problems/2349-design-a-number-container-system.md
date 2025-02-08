```cpp
class NumberContainers {
    unordered_map<int, int> idxToValue;
    unordered_map<int, set<int>> valueToIdx;
public:
    NumberContainers() {
        idxToValue.clear();
        valueToIdx.clear();
    }
    
    void change(int index, int number) {
        if (idxToValue.contains(index)) {
            const int oldValue = idxToValue[index];
            set<int>& indices = valueToIdx[oldValue];
            indices.erase(index); // O(log N)
            if (indices.empty()) {
                valueToIdx.erase(oldValue);
            }
        }
        idxToValue[index] = number;
        valueToIdx[number].insert(index);
    }
    
    int find(int number) {
        if (valueToIdx.contains(number)) {
            return *valueToIdx[number].begin();
        }
        return -1;
    }
};

/**
 * Your NumberContainers object will be instantiated and called as such:
 * NumberContainers* obj = new NumberContainers();
 * obj->change(index,number);
 * int param_2 = obj->find(number);
 */
 ```
 
