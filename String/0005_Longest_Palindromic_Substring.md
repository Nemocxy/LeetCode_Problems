## **05. Longest Palindromic Substring**

[LeetCode 05. Longest Palindromic Substring [Medium]](https://leetcode.com/problems/longest-palindromic-substring/description/)

Given a string `s`, return the **longest palindromic substring** in `s`.



```markdown
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```

```markdown
Input: s = "cbbd"
Output: "bb"
```

Constraints:

* `1 <= s.length <= 1000`
* s consist of only digits and English letters.


### **Solution**
* We can check the longest palindromic substring by starting from the **middle**. For each character, we regard it as the middle point and expand our left and right pointer to compare the characters.

* For every character, we check twice to see if it is an odd or even length substring.

* If the length of the new substring is greater than the old one, we update the result. 


Language: `C++`
``` C++
class Solution {
public:
    string longestPalindrome(string s) {
        string result = "";

        for (int i = 0; i < s.length(); i++) {
            //case 1: odd length substring
            int left = i;
            int right = i;
            while (left >= 0 && right < s.length() && s[left] == s[right]) {
                int sub_len = right - left + 1;
                if (result.length() < sub_len) {
                    result = s.substr(left, sub_len);
                }
                left--;
                right++;
            }

            //case 2: even length substring
            left = i;
            right = i + 1;
            while (left >= 0 && right < s.length() && s[left] == s[right]) {
                int sub_len = right - left + 1;
                if (result.length() < sub_len) {
                    result = s.substr(left, sub_len);
                }
                left--;
                right++;
            }
        }

        return result;
    }
};
```
### **Complexity**
* **Time：O(n^2)**
* **Space：O(n)**
