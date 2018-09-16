Data Structure
==
## Priority Queue
function |heap | array | Fibonacci heap
-|-|-|- 
insert(item, priority) | O(Logn) | O(1) | O(1)
getHighestPriority() | O(1) | O(n) | O(1)
deleteHighestPriority() | O(Logn) | O(n) | O(Logn)

## Heap
### Binary Heap
1) getMini(): It returns the root element of Min Heap. Time Complexity of this operation is O(1).

2) extractMin(): Removes the minimum element from MinHeap. Time Complexity of this Operation is O(Logn) as this operation needs to maintain the heap property (by calling heapify()) after removing root.

3) decreaseKey(): Decreases value of key. The time complexity of this operation is O(Logn). If the decreases key value of a node is greater than the parent of the node, then we don’t need to do anything. Otherwise, we need to traverse up to fix the violated heap property.

4) insert(): Inserting a new key takes O(Logn) time. We add a new key at the end of the tree. IF new key is greater than its parent, then we don’t need to do anything. Otherwise, we need to traverse up to fix the violated heap property.

5) delete(): Deleting a key also takes O(Logn) time. We replace the key to be deleted with minum infinite by calling decreaseKey(). After decreaseKey(), the minus infinite value must reach root, so we call extractMin() to remove the key.

* building: O(n)
* heapify: O(Logn)
* heapsort: O(nLogn)
* [link](https://stackoverflow.com/questions/9755721/how-can-building-a-heap-be-on-time-complexity)

### Binomial Heap
### Fibonacci Heap
### Paring Heap
### LinkedHashMap
### TreeMap