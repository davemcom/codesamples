## 3Sum
#### medium
Given an array nums of *n* integers, are there elements *a, b, c* in nums such that `a + b + c = 0`? Find all unique triplets in the array which gives the sum of zero.

##### Note:

The solution set must not contain duplicate triplets.



### Example:

```javascript
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

### Solution
```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */

var compare = function(a, b){
    if(a<b){
        return -1;
    }
    if(a>b){
        return 1; 
    }
    return 0;
}
var threeSum = function(nums) {
    set = nums.sort(compare);
    retv = {};
    
    bag = {};
    col = [];
    for(var i = 0; i<set.length; i++){
        if(bag[set[i]]===undefined){
            bag[set[i]]=0;
        }
        bag[set[i]]++;
        if(bag[set[i]]<=3){
          col.push(set[i]);
        }
    }
    
    for(var i = 0; i<col.length; i++){
        a = col[i];
        if(a>0){
          break;
        }
        
        for(var j =col.length-1; j>i; j--){
            b = col[j];
            need = -(a+b);
    
            if(bag[need]===undefined){
                continue;
            }
            avail_c = bag[need];
            if((a==need && b==need) && avail_c < 3){
                continue;
            }else if((a==need || b==need) && avail_c<2){
                continue;
            }
            sol = [a,b,need].sort(compare);                
            
            retv[sol.join('')] = sol;
        }
    }
    
    return Object.values(retv);
};
```