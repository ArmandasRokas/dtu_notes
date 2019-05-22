## Algorithms

### Find peak

- Peak is as least as large as it's neighbors
- Can be done recursively with running time: $O(\log{}n)$ 

### Binary search

- Given **sorted array** `A` and number `x`, determine if `x`, appears in the array
- Running time: $O(\log{}n)$

### Insertion sort

- Given array return array with same values as A but in sorted order
- Running time:  $O(n^2)$ 

### Merge sort

- Recursive sorting via merging sorted subarrays
- Example of Divide and Conquer 
  - Divide. Split array into halves
  - Conquer. Sort each half
  - Combine. Merge halves
- Running time: $O(n\log{}n)$