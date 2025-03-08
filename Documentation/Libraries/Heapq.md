[⬅](../../README.md)
# Heapq Documentation
## Contents
- [Details](#details)
- [Methods](#methods)
  - [Heappush](#heappush)
  - 

[🔼](#Heapq-documentation)
## Details

This module provides an implementation of the heap queue algorithm, also known as the priority queue algorithm.

Heaps are binary trees for which every parent node has a value less than or equal to any of its children. 
We refer to this condition as the heap invariant.

This implementation uses arrays for which heap[k] <= heap[2*k+1] and heap[k] <= heap[2*k+2] for all k, counting elements from zero. 
For the sake of comparison, non-existing elements are considered to be infinite. 
The interesting property of a heap is that its smallest element is always the root, heap[0].

The API below differs from textbook heap algorithms in two aspects: (a) We use zero-based indexing. 
This makes the relationship between the index for a node and the indexes for its children slightly less obvious, 
but is more suitable since Python uses zero-based indexing. (b) Our pop method returns the smallest item, not the largest 
(called a “min heap” in textbooks; a “max heap” is more common in texts because of its suitability for in-place sorting).

These two make it possible to view the heap as a regular Python list without surprises: 
heap[0] is the smallest item, and heap.sort() maintains the heap invariant!

[🔼](#Heapq-documentation)
## Methods

[🔼](#Heapq-documentation)
### Heappush

```python
heapq.heappush(heap, item)
```
Push the value item onto the heap, maintaining the heap invariant.

