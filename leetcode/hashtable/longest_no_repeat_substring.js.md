## Longest Substring Without Repeating Characters
#### medium


Given a string, find the length of the longest substring without repeating characters.

### Example 1:

Input: `"abcabcbb"`
Output: `3` 
Explanation: The answer is `"abc"`, with the length of `3`. 

### Example 2:

Input: `"bbbbb"`
Output: `1`
Explanation: The answer is `"b"`, with the length of `1`.

### Example 3:

Input: `"pwwkew"`
Output: `3`
Explanation: The answer is `"wke"`, with the length of `3`. 

##### Note
 that the answer must be a substring, "pwke" is a subsequence and not a substring.

### Solution:

```javascript

/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    var accum = {};
    var longestString = '';
    var testString = '';
    var foundAt = '';
    for(i = 0; i < s.length; i++){
        char = s[i];
        foundAt = testString.indexOf(char);
        // console.log(`${i} testing '${char}' within "${testString}"`);

        if(foundAt!==-1){
         // console.log(`Found another '${char}'  @ ${foundAt} in '${testString}', cutting string at earlierst '${char}'`);
            testString = testString.slice(foundAt+1,testString.length);
        }
        // console.log(`adding ${char} to "${testString}"`);
        testString += char;
        // console.log(`current Test String = "${testString}"`);

        if(testString.length > longestString.length){
           longestString = testString; 
        }
    }
     // console.log(longestString);
    return longestString.length;
};


```