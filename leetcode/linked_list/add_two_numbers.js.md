## Add Two Numbers
#### medium
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example:

Input: `(2 -> 4 -> 3) + (5 -> 6 -> 4)`

Output: `7 -> 0 -> 8`

Explanation: `342 + 465 = 807`

### Solution
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */

var mkNode = function(val){
    return {val: val, next: null}
}


var addTwoNumbers = function(l1, l2) {
    var carry = 0;
    var retvRoot = mkNode(0);
    var curr = retvRoot;
    var x = l1;
    var y = l2;
        
    while(x!==null || y!==null){
        var vx = x===null ? 0 : x.val;
        var vy = y===null ? 0 : y.val;
        var total = vx + vy + carry;
        
        val = total < 10 ? total : total - 10;
        carry = total > 9 ? 1 : 0;

        curr.next = mkNode(val);
        curr = curr.next;
        
        if(x!==null){
            x = x.next;
        }
        if(y!==null){
            y = y.next;
        }
    }
    if(carry){
        curr.next = mkNode(carry);
    }
    
    return retvRoot.next;
};




```