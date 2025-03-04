# Disjoint Set Union Template

With path compression (problem: https://leetcode.com/problems/number-of-provinces)

```cpp
class DisjointSetUnion {
private:
    vector<int> parent;
    vector<int> setSize;
public:
    DisjointSetUnion(int size) {
        parent = vector<int>(size);
        setSize = vector<int>(size);
        for (int i = 0; i < size; ++i) {
            parent[i] = i;
            setSize[i] = 1;
        }
    }

    int findRoot(int idx) {
        if(parent[idx] != idx) {
            // apply path compression
            parents[idx] = findRoot(parent[idx]);
        }
        return idx;
    }

    void unionSets(int idx1, int idx2) {
        int root1 = findRoot(idx1);
        int root2 = findRoot(idx2);

        if (root1 == root2) return;

        if (setSize[root2] > setSize[root1]) {
            parent[root1] = root2;
            setSize[root2] += setSize[root1];
        } else {
            parent[root2] = root1;
            setSize[root1] += setSize[root2];
        }
    }

};

class Solution {
public:
    int findCircleNum(vector<vector<int>>& M) {
        int n = M.size();
        DisjointSetUnion* dsu = new DisjointSetUnion(n);
        int c = n;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (M[i][j] == 1 and dsu->findRoot(i) != dsu->findRoot(j)) {
                    dsu->unionSets(i, j);
                    --c;
                }
            }
        }

        return c;
    }
};
```
