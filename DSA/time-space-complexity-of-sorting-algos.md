# Time and Space Complexity of Sorting Algorithms

_Read with proper latex rendering: https://csposts.com/dsa/time-and-space-complexities-of-popular-sorting-techniques

| Sort | Worst Case TC | Avg Case TC | Best Case TC | Space Complexity | Is Stable |
|------|---------------|-------------|--------------|------------------|-----------|
| Bubble Sort | $O(N^2)$ | $\Theta(N)$ | $\Omega(N)$ | $O(1)$ | Yes |
| Selection Sort | $O(N^2)$ | $\Theta(N^2)$ | $\Omega(N^2)$ | $O(1)$ | No[^1] |
| Insertion Sort | $O(N^2)$ | $\Theta(N^2)$ | $\Omega(N)$ | $O(1)$ | Yes |
| Merge Sort | $O(N logN)$ | $\Theta(N logN)$ | $\Omega(N logN)$ | $O(N)$ | Yes |
| Quick Sort | $O(N^2)$ | $\Theta(N logN)$ | $\Omega(N logN)$ | $O(N), O(logN)$| No |
| Heap Sort | $O(N logN)$ | $\Theta(N logN)$ | $\Omega(N logN)$ | $O(1)$ | No[^1] |
| Counting Sort | $O(N + R)$ | $\Theta(N + R)$ | $\Omega(N + R)$ | $O(R)$ | Yes |

[^1]:
    The default implementation is not stable, however it can be made stable
    using some special technique.
