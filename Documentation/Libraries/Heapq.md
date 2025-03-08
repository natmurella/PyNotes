[⬅](../../README.md)
# Heapq Documentation
## Contents
- [Details](#details)
  - [Heap Description](#heap-description)
  - [Python Heap Documentation](#python-heap-documentation)
- [Methods](#methods)
  - [Heappush](#heappush)
  - 

[🔼](#Heapq-documentation)
## Details

[🔼](#Heapq-documentation)
### Heap Description

A Heap is a complete binary tree data structure that satisfies the heap property: 
for every node, the value of its children is greater than or equal to its own value. 
Heaps are usually used to implement priority queues, where the smallest (or largest) 
element is always at the root of the tree.

Heap Data Structure is generally taught with Heapsort. Heapsort algorithm has limited uses because Quicksort is better in practice. 
Nevertheless, the Heap data structure itself is enormously used. 

1. Priority Queues: Heaps are commonly used to implement priority queues, where elements with higher priority are extracted first. This is useful in many applications such as scheduling tasks, handling interruptions, and processing events.
2. Sorting Algorithms: Heapsort, a comparison-based sorting algorithm, is implemented using the Heap data structure. It has a time complexity of O(n log n), making it efficient for large datasets.
3. Graph algorithms: Heaps are used in graph algorithms such as Prim’s Algorithm, Dijkstra’s algorithm., and the A* search algorithm.
4. Lossless Compression: Heaps are used in data compression algorithms such as Huffman coding, which uses a priority queue implemented as a min-heap to build a Huffman tree.
5. Medical Applications: In medical applications, heaps are used to store and manage patient information based on priority, such as vital signs, treatments, and test results.
6. Load balancing: Heaps are used in load balancing algorithms to distribute tasks or requests to servers, by processing elements with the lowest load first.
7. Order statistics: The Heap data structure can be used to efficiently find the kth smallest (or largest) element in an array. See method 4 and 6 of this post for details.
8. Resource allocation: Heaps can be used to efficiently allocate resources in a system, such as memory blocks or CPU time, by assigning a priority to each resource and processing requests in order of priority.
9. Job scheduling: The heap data structure is used in job scheduling algorithms, where tasks are scheduled based on their priority or deadline. The heap data structure allows efficient access to the highest-priority task, making it a useful data structure for job scheduling applications.

[🔼](#Heapq-documentation)
### Python Heap Documentation

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

