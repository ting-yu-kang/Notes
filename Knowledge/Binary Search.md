# Binary Search:
There are 2 types of binary search to deal with when `array[mid] == target`
* `bisect_left`: point to the **first occurrance of the target**
* `bisect_right`: point to the **next of last occurrance of the target**

for example:
`[1, 2, 3, 3, 3, 4, 5, 6], target = 3`

`bisect_left` should return idx = 2
`bisect_right` should return idx = 5

in this case in binary search we can see:
```
left = 0
right = len(arr)
if target < arr[mid]:
    right = mid
if arr[mid] < target:
    left = mid + 1
```
the only difference would be:
```
if arr[mid] == target
#bisect_left
    right = mid
#bisect_right
    left = mid + 1
```

and both will return `left`

If we want to return the index of target,
use `bisect_left` and return `left`, or use `bisect_right` and return `left - 1` (if target exists)

* `bisect_left` points to the target if target exists
* `bisect_right` never points to the target, but the insertion point of target (last insertion point)