## **74. Search a 2D Matrix**

[LeetCode 77. Combinations [Medium]](https://leetcode.com/problems/combinations/description/)

Given two integers `n` and `k`, return all possible combinations of `k` numbers chosen from the range `[1, n]`.

You may return the answer in **any order**.

```markdown
Input: n = 4, k = 2
Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
Explanation: There are 4 choose 2 = 6 total combinations.
Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination.
```

```markdown
Input: n = 1, k = 1
Output: [[1]]
Explanation: There is 1 choose 1 = 1 total combination.
```


### **Solution**
* We could create a temp list and keep push the element `i (i < n)` to the list until it reaches a size of `k`. Then we push the temp list to the final big list.

* `i = the last element in the temp list + 1`

* In the end of the **recursion**, the final list should contain all the combinations of n choose k.


Language: `C++`
``` C++
class Solution {
public:
    vector<vector<int>> result;

    vector<vector<int>> combine(int n, int k) {
        vector<int> tempList;
        helper(tempList, n, k, 1);
        return result;
    }

    void helper(vector<int> &tempList, int num, int len, int index) {
        if (tempList.size() == len) {
            result.push_back(tempList);
            return;
        }
        for (int i = index; i <= num; i++) {
            tempList.push_back(i);
            helper(tempList, num, len, i + 1);
            tempList.pop_back();
        }
    }

};
```
### **Complexity**
* **Time：O(n!)**
* **Space：O(n)**
