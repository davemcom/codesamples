## Two Sum
#### easy
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given   `nums = [2, 7, 11, 15], target = 9`,

Return `[0, 1]`

Because `nums[0] + nums[1] = 2 + 7 = 9`,

### Solution
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for(var a = 0; a<nums.length-1; a++){
        for(var b = a+1; b<nums.length; b++ ){
            if(nums[a]+nums[b]==target){
                return [a,b];
            }
        }
    }
}
```