## Add Binary
#### easy
Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.

### Example 1:

Input: `a = "11", b = "1"`
Output: `"100"`

### Example 2:

Input: `a = "1010", b = "1011"`
Output: `"10101"`

### Solution

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    var posA = a.length-1;
    var posB = b.length-1;
    var carry = 0;
    var answer = '';
    while(posA>=0 || posB>=0){
        A = posA>=0 ? a[posA]==1 ? 1 : 0 : 0;
        B = posB>=0 ? b[posB]==1 ? 1 : 0 : 0;
        
        sum = A + B + carry;
        carry = (sum > 1) ? 1 : 0;
        answer = ((sum==1 ||sum==3) ? 1 : 0) + answer;
        
        if(posA>=0){
            posA--
        }
        if(posB>=0){
            posB--
        }
    }
    if(carry){
        answer = carry + answer;
    }
    return answer;
};
```
