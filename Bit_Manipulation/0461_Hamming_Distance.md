## **461. Hamming Distance**

[LeetCode 0461. Hamming Distance [Easy]](https://leetcode.com/problems/hamming-distance/description/)

The Hamming distance between two integers is the number of positions at which the corresponding bits are **different**.

Given two integers x and y, return the `Hamming distance` between them.



```markdown
Input: x = 1, y = 4
Output: 2
Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑
The above arrows point to positions where the corresponding bits are different.
```

```markdown
Input: x = 3, y = 1
Output: 1
```

Constraints:

* `0 <= x, y <= 2^31 - 1`

### **Solution**
* We could use **exclusive or (XOR)** on x and y to get an integer z that contains all the different bits.
* By going through bits in z we could count the hamming distance between x and y.


Language: `C++`
``` C++
class Solution {
public:
    int hammingDistance(int x, int y) {
        int z = x^y; // z = binary exclusive OR, O(1) time
        int count = 0;
        while (z > 0) {
            if (z % 2 == 1) {
                count++;
            }
            z = z / 2;
        }
        return count;
    }
};
```
### **Complexity**
* **Time：O(n)**
* **Space：O(1)**
