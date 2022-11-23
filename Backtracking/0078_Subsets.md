## **78. Subsets**

[LeetCode 78. Subsets [Medium]](https://leetcode.com/problems/subsets/description/)

Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.



```markdown
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

```markdown
Input: nums = [0]
Output: [[],[0]]
```


### **Solution**


Language: `C++`
``` C++
class Solution {
public:
    vector<vector<int>> result;

    vector<vector<int>> subsets(vector<int>& nums) {
        vector<int> tempList;

        for (int i = 1; i <= nums.size(); i++) {
            helper(tempList, nums, i, 0);
        }

        result.push_back({});
        return result;
    }

    void helper(vector<int>& tempList, vector<int>& num, int len, int index) {
        if (tempList.size() == len) {
            result.push_back(tempList);
            return;
        }
        for (int i = index; i < num.size(); i++) {
            tempList.push_back(num[i]);
            helper(tempList, num, len, i + 1);
            tempList.pop_back();
        }
    }
};
```
### **Complexity**
* **Time：O(n!)**
* **Space：O(n)**
