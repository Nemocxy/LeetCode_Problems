## **02. Add Two Numbers**

[LeetCode 02. Add Two Numbers [Medium]](https://leetcode.com/problems/add-two-numbers/description/)

You are given two `non-empty` linked lists representing two non-negative integers. The digits are stored in `reverse order`, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.



```markdown
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

```markdown
Input: l1 = [0], l2 = [0]
Output: [0]
```

```markdown
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```
Constraints:

* The number of nodes in each linked list is in the range `[1, 100]`.
* `0 <= Node.val <= 9`
* It is guaranteed that the list represents a number that does not have leading zeros.

### **Solution**
* We create a new linked list to record the result and a pointer to point at the current node we are accessing.
* By adding the numbers at the same position in l1 and l2, we get a `sum`.
* Then we add the carry over number to the sum.
* Therefore,\
 `new node value = sum % 10`\
`new carry over number = sum / 10`.


Language: `C++`
``` C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *result = new ListNode(-1);
        ListNode *curr_pos = result;
        int carry_over = 0;

        while (l1!=NULL || l2!=NULL || carry_over == 1) {
            int sum = 0;
            if (l1 != NULL) {
                sum += l1->val;
                l1 = l1->next;
            }
            if (l2 != NULL) {
                sum += l2->val;
                l2 = l2->next;
            }
            sum += carry_over;
            ListNode *result_new = new ListNode(sum % 10);
            curr_pos->next = result_new;
            curr_pos = curr_pos->next;

            carry_over = sum / 10;
        }
        return result->next;
    }
};
```
### **Complexity**
* **Time：O(max(n, m))**
* **Space：O(max(n, m))**\
where n = l1.length, m = l2.length
