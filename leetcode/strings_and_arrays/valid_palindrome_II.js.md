## Valid Palindrome II
#### easy
Given a non-empty string `s`, you may delete **at most** one character. Judge whether you can make it a palindrome.

### Example 1:
Input: "aba"

Output: True

### Example 2:
Input: "abca"

Output: True

Explanation: You could delete the character 'c'.

### Note:
The string will only contain lowercase characters a-z. The maximum length of the string is 50000.



### Solution:

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
    clean = s.replace(/\W/g, '').toLowerCase();
    console.log(clean);
    if(clean.length % 2){
        // odd, ignore middle one.
        lower_end = Math.floor(clean.length / 2)-1;
        upper_start = lower_end+2;
    }else{
        lower_end = Math.floor(clean.length / 2);
        upper_start = lower_end+1;
    }
    for(var i = 0; i<=lower_end; i++){
        if(clean[i]!=clean[clean.length-1-i]){
            return false;
        }
    }
    return true;
};
```
