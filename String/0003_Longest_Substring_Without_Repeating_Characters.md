## **03. Longest Substring Without Repeating Characters**

[LeetCode 03. Longest Substring Without Repeating Characters [Medium]](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

Given a string `s`, find the length of the **longest substring** without repeating characters.



```markdown
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

```markdown
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

```markdown
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
Constraints:

* `0 <= s.length <= 5 * 10^4`
* s consists of English letters, digits, symbols and spaces.

### **Solution**
* We could use **frequency map** to record characters.

* When traversing the string `s`, we use integer `j` as a "pointer" to point at the start of the current substring.

* When there is a repeated character, we "pop" out the character at j, j++, until the repeated character is "poped" out, and record the max length.


Language: `C++`
``` C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int result = 0;
        int temp = 0;
        int j = 0;

        map<char, int> m;
        for (int i = 0; i < s.length(); i++) {
            m[s[i]]++;
            temp++;

            while (m[s[i]] > 1) {
                m[s[j]]--;
                j++;
                temp--;
            }
            result = max(temp, result);
        }
        return result;
    }
};
```
### **Complexity**
* **Time：O(n^2)**
* **Space：O(n)**
