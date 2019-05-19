## Merge two sorted lists
#### easy
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.


### Example:

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

### Solution
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
  
    if(l1==null && l2!=null){
        return l2;
    }else if(l1!=null && l2==null){
        return l1;
    }
    
    var prev_p = null;
    var root = l1; 
    var p = root;
    
    var q = l2;
    done = false;
  
    while(!done && q!==null){
        if(p === null){
            // console.log(`${q.val} but p is null `);
            // Add this Q to end of list
            prev_p.next = {
                val: q.val,
                next: q.next
            }
            // unlink q.next so a cleanup process
            // doesn't delete the end of "P"
            q.next = null; 
            
            // DONE: we've just pinned the remainder of Q on to P.
            done = true;
        }else if(p.val <= q.val){
            // console.log(`${q.val} <= ${p.val}`);

            // continue
            prev_p = p;
            p = p.next;
            continue;
        }else{
          // insert Q Before this one...
          if(prev_p==null){
            // console.log(`${q.val} as new head `);
              // insert as first node...
              var new_head = {
                  val: q.val,
                  next: p
              }
              root = new_head;
              q = q.next;
              prev_p = new_head;
          }else{
              // console.log(`insert ${q.val} before ${p.val}`)
              prev_p.next = {
                  val: q.val,
                  next: p
              }
              prev_p = prev_p.next;

              q = q.next;
          }
        }
    }
    return root;
};

```