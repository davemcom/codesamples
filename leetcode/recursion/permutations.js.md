## Permutations
#### medium
Given a collection of distinct integers, return all possible permutations.

Example:

Input: `[1,2,3]`
Output:
```javascript
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

### Solution:
```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
    var words = [];

    for(var i = 0; i<nums.length; i++){
        
        var num = nums[i];

        if(nums.length > 1){
            var subwords = permute(nums.filter((n)=>n!==num));
            // console.log(`subwords ${subwords}`);
            for(var k = 0; k < subwords.length; k++ ){
                // console.log(subwords[k]);
                subwords[k].unshift(num)
                words.push(subwords[k]);
            }
        }else{
            words.push([num]);
        }
    }
    
    return words;
};


```