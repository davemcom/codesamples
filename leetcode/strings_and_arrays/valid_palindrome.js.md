## Valid Palindrome
#### easy
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

### Example 1:

Input: "A man, a plan, a canal: Panama"
Output: true

### Example 2:

Input: "race a car"
Output: false


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
