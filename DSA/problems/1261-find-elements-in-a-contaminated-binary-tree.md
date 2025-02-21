Standard tree traversal. Do not modify the input in general.

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class FindElements {
    unordered_set<int> treeValues;
public:
    FindElements(TreeNode* root) {
        stack<pair<TreeNode*, int>> nodes;
        nodes.push({root, 0});

        while(!nodes.empty()) {
            auto [cur, val] = nodes.top(); nodes.pop();
            treeValues.insert(val);

            if (cur->left != nullptr) {
                nodes.push({cur->left, 2 * val + 1});
            }
            if (cur->right != nullptr) {
                nodes.push({cur->right, 2 * val + 2});
            }
        }

    }
    
    bool find(int target) {
        return treeValues.contains(target);
    }
};

/**
 * Your FindElements object will be instantiated and called as such:
 * FindElements* obj = new FindElements(root);
 * bool param_1 = obj->find(target);
 */
```
