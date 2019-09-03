## Memory corruption
* When the contents of a memory location are modified due to programmatic behavior that **exceeds the intention of the original programmer or program/language constructs**; this is termed violating memory safety.

```c
char* p=new char[5];
strcpy(p,"aaaaa"); 
delete[] p;
```

* 這段代碼就會出錯,因為申請了一個size為5的內存,
但是strcpy過去了一個size為6的字符串,
因此破壞了這個指針.

## Deadlock
* Deadlock can arise if following four conditions hold simultaneously (Necessary Conditions) 
1. **Mutual Exclusion:**\
One or more than one resource are non-sharable (Only one process can use at a time)

2. **Hold and Wait:**\
 A process is holding at least one resource and waiting for resources.

3. **No Preemption:**\
A resource cannot be taken from a process unless the process releases the resource.

4. **Circular Wait:**\
A set of processes are waiting for each other in circular form.

## Big endian vs litte endian
* [link](https://notfalse.net/19/byte-order)
* 0x12345678
    Addr | big-endian | little-endian
    --|--|--
    |0x0000	| 0x12 | 0x78
    |0x0001	| 0x34 | 0x56
    |0x0002 | 0x56 | 0x34
    |0x0003 | 0x78 | 0x12
* Compare
    compare | big-endian | little-endian
    -|-|-
    advantage | easy for human to read | different type of data can have the same base

## GB vs GiB
* 1GB = 10^9 = 1,000,000,000 bytes
* 1GiB = 2^30 = 1,073,741,824 bytes

## Minimum Spanning Tree

### Kruskal's Algorithm
* Sort Edges: `O(|E|log|E|)`
* Connect different groups of vertices: `O(|V|log|V|)`
    * `|V|`: loop through all vertices
    * `log|V|`: union find
* Time complexity: `O(|V|log|V|) + O(|E|log|E|) = O(|E|log|E|)`

### Prime's Algorithm
* Min-heap for vertices by distance: `O(|V|log|V|)`
    * `|V|`: all all vertices
    * `log|V|`: heapify
* Update the distance of vertices: `O(|E|log|V|)`
    * `|E|`: loop through all edges
    * `log|V|`: heapify
* Time complexity: `O(|V|log|V|) + O(|E|log|V|) = O(|E|log|V|)`

## 25 horses
* [link](https://hxraid.iteye.com/blog/662643?fbclid=IwAR0KwZ4EH-0xjlTsRQ985rgOuhbcG5w0nRUVr9eZF2kLqkYR3KzdcPdFKtY)
* From 10 -> 8 or 9

## Double
* `Double.MIN_VALUE` is positive!
* Use `-Double.MAX_VALUE` instead.

## 三步翻轉法
* String rotate
    * rotate left
    * rotate right
    * rotate all

## Open hashing vs close hashing
* In Open Hashing each cell in the array points to a list containg the collisions. The hashing has produced the same index for all items in the linked list.

* In Closed Hashing (open addressing) you use only one array for everything. You store the collisions in the same array. The trick is to use some smart way to jump from collision to collision unitl you find what you want. And do this in a reproducible / deterministic way.