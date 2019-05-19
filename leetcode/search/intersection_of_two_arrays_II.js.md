## Intersection of Two Arrays II
#### easy
Given two arrays, write a function to compute their intersection.

### Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]

### Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
Note:

Each element in the result should appear as many times as it shows in both arrays.
The result can be in any order.

#### Follow up:

What if the given array is already sorted? How would you optimize your algorithm?
What if nums1's size is small compared to nums2's size? Which algorithm is better?
What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

### Solution: 
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    n1 = getHashTally(nums1);
    n2 = getHashTally(nums2);
    caught = {};
    retv = [];
    for(var i in nums1){
        c = nums1[i];
        if(n2[c] && caught[c]==undefined){
            qty = n2[c] > n1[c] ? n1[c] : n2[c];
            caught[c] = true;
            for(var j = 0; j<qty; j++){
                retv.push(c);
            }
        }
    }
    return retv;
};

var getHashTally = function(a){
    var tally = {};
    for(var i in a){
        if(tally[a[i]]===undefined){
            tally[a[i]]=1;
        }else{
            tally[a[i]]++;
        }
    }
    return tally;
}

```