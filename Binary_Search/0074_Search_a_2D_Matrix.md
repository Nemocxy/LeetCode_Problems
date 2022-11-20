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


### **Solution**
* We could treat the matrix as an array so that to access the matrix: \
`the row # = mid / total col #`\
`the col # = mid % total col #`

* When applying **binary research**, let: \
`mid = left pt + right pt / 2`\
when mid < target, we take the second half:\
`left pt = mid + 1`\
when mid > target, we take the first half:\
`right pt = mid - 1`\
when mid == target, return true, otherwise return false.

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
### **Complexity**
* **Time：O(log(m*n))**
* **Space：O(1)**
