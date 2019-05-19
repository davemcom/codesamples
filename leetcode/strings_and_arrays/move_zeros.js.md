## Move Zeroes
#### easy
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

### Example:

Input: `[0,1,0,3,12]`
Output: `[1,3,12,0,0]`

#### Note:

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

### Solution

````javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    zerosFound = 0;
    for(var i=0; i<nums.length; i++){
        if(nums[i]==0){
            zerosFound++;
        }else if(zerosFound){
            // shift left
            nums[i-zerosFound] = nums[i];
            nums[i] = 0;
        }
    }
    return nums;
};
```