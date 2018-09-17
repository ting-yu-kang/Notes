Sort
==
Algorithm |Time(best)|Time(avg)|Time(worse)|Space|Stability 
--- | --- | --- | --- | --- | ---
Heap Sort|`Ω(nlog(n))`|`Θ(nlog(n))`|`O(nlog(n))` | `O(1)` | X
Quick Sort|`Ω(nlog(n))`|`Θ(nlog(n))`|`O(nlog(n))` | `O(log(n))` | X
Merge Sort|`Ω(nlog(n))`|`Θ(nlog(n))`|`O(n^2)` | `O(n)` | O

## Heap Sort
[link](https://www.geeksforgeeks.org/heap-sort/)

* Quick
    * 整體有序 -> 局部有序
    * T(n) = O(n) + T(n/2)
* Merge
    * 局部有序 -> 整體有序
    * T(n) = T(n/2) + O(n)