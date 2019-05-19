## Letter Combinations of a Phone Number
#### medium

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

### Example:

Input: `23`

Output: `["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]`

##### Note:

Although the above answer is in lexicographical order, your answer could be in any order you want.

### Solution:
```javascript

/**
 * @param {string} digits
 * @return {string[]}
 */
var mappings = {
    1: [],
    2: 'abc'.split(''),
    3: 'def'.split(''),
    4: 'ghi'.split(''),
    5: 'jkl'.split(''),
    6: 'mno'.split(''),
    7: 'pqrs'.split(''),
    8: 'tuv'.split(''),
    9: 'wxyz'.split(''),
    0: [],
}


var letterCombinations = function(digits) {
    if(!digits){
        return [];
    }
    return getStrings('', digits, 0);
};

// prefix = string
// remaining = array
// returns an array of strings
var getStrings = function(prefix, digits, pos){
    var digit = digits[pos];
    var letters = mappings[digit];
    var retv = [];
    var len = letters.length;
    for(var i = 0; i<len; i++){
        str = '' + prefix + letters[i];
        if(pos===digits.length-1){  
            retv.push(str);
        }else{
            subs = getStrings(str , digits, pos+1);
            for(var j = 0; j<subs.length; j++){
                retv.push(subs[j]);
            }
        }
    }
    return retv;
    
}
```
