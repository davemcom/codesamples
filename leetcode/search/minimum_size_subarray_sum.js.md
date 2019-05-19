## Minimum Size Subarray Sum
#### medium

Given an array of `n` positive integers and a positive integer s, find the minimal length of a **contiguous** subarray of which the sum `≥ s`. If there isn't one, return 0 instead.

### Example: 
```
Input: s = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: the subarray [4,3] has the minimal length under the problem constraint.
```
#### Follow up:
If you have figured out the O(n) solution, try coding another solution of which the time complexity is *O(n log n)*. 

### Solution:
```javascript
/**
 * @param {number} s
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function(s, nums) {
    
    best_length = null;
    sol = [];
    curTtl = 0;
    bestSol = [];
    for(var i = 0; i<nums.length; i++){
        val = nums[i];
        sol.push(val);
        curTtl += val;
        
        if(best_length===null && curTtl>=s){
            bestSol = sol;
            best_length = sol.length;
        }

        while(curTtl>=s){
            
            
            if((curTtl - sol[0]) >=s){
                curTtl -= sol.shift();

                if(sol.length < best_length){
                    best_length = sol.length;
                    bestSol = sol;
                }
            }else{
                break;
            }   
        }
    }
    return best_length === null ? 0 : best_length;
};


```