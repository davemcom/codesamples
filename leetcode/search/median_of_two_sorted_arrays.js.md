
## Median of Two Sorted Arrays
#### hard

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be *O(log (m+n))*.

You may assume `nums1` and `nums2` cannot be both empty.

### Example 1:
```javascript
nums1 = [1, 3]
nums2 = [2]
```
The median is 2.0

### Example 2:

```javascript

nums1 = [1, 2]
nums2 = [3, 4]
```
The median is (2 + 3)/2 = 2.5

### Solution
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
function compare(a, b) {
  if (a < b) {
    return -1;
  }
  if (a > b) {
    return 1;
  }
  // a must be equal to b
  return 0;
}

var findMedianSortedArrays = function(nums1, nums2) {
    if(nums1.length && nums2.length){
        nums = nums1.concat(nums2);
        sorted = nums.sort(compare);
        // console.log(sorted);
        return getMedian(sorted);
        
    }else if(nums1.length){
        return getMedian(nums1);
    }else{
        return getMedian(nums2);
    }
};

function getMedian(nums){
    if(!nums.length){
        
        return 0;
    }
    
    if(nums.length % 2){
        // is odd
        return nums[Math.ceil(nums.length/2)-1];
    }
    
    // is even
    // console.log(`nums.length = ${nums.length}`);
    center = nums.length/2;
    // console.log(`center = ${center}`);
   
    var sum = nums[center-1] + nums[center];
    // console.log(`sum = ${sum}`);
    
    var median = (sum)/2;
    // console.log(`median = ${median}`);
    
    return median;
}
```