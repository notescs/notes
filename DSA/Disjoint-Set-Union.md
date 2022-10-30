# Disjoint Set Union Template

With path compression (problem: https://leetcode.com/problems/number-of-provinces)

```cpp
class Solution {
public:
    int root(int arr[], int i) {
        while(arr[i] != i) {
            arr[i] = arr[arr[i]];
            i = arr[i];
        }
        return i;
    }
    void union_(int arr[], int size[], int a, int b) {
        int root_a = root(arr, a);
        int root_b = root(arr, b);
        if (root_a != root_b) {
            if (size[root_a] < size[root_b]) {
                arr[root_a] = arr[root_b];
                size[root_b] += size[root_a];
            } else {
                arr[root_b] = arr[root_a];
                size[root_a] += size[root_b];
            }
        }
    }
    bool find(int arr[], int a, int b) {
        int root_a = root(arr, a);
        int root_b = root(arr, b);
        return root_a == root_b;
    }
    int findCircleNum(vector<vector<int>>& M) {
        int n = M.size();
        int arr[n], size[n];
        for (int i = 0; i < n; i++) {
            arr[i] = i;
            size[i] = 1;
        }
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (M[i][j] == 1)
                    union_(arr, size, i, j);
            }
        }
        int c = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] == i) {
                c++;
            }
        }
        return c;
    }
};
```