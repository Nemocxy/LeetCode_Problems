## **74. Search a 2D Matrix**

[LeetCode 74. Search a 2D Matrix [Medium]](https://leetcode.com/problems/search-a-2d-matrix/description/)

Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:

Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.

```markdown
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true
```

```markdown
Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false
```

### **思路**
* **因为 `matrix` 内的数字是按顺序排列 所以可以将 `2D matrix` 看作普通 `1D list` 来进行 `binary search` 再将其转换回 `2D` 即可 `(mid_point -> mid_row, mid_col)`**

### **代码**

``` JavaScript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
    var rowL = 0;
    var rowR = matrix.length * matrix[0].length - 1;
    console.log(rowR);

    while (rowL <= rowR) {
        var mid = Math.floor((rowL + rowR) / 2);
        console.log("mid is:" + mid);

        var row = Math.floor(mid / matrix[0].length);
        var col = mid % matrix[0].length;
        if (matrix[row][col] == target) {
            return true;
        } else if (matrix[row][col] < target) {
            rowL = mid + 1;
            console.log("left is: "+ rowL);
        } else {
            rowR = mid - 1;
            console.log("right is: "+ rowR);
        }
    }

    return false;

};
```
### **复杂度分析**
* **时间复杂度：O(log(m*n))**
* **空间复杂度：O(1)**
