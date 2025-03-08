# Heapq Documentation
[⬅](../../README.md)

## Contents
- [Details](#details)
  - [Heap Description](#heap-description)
  - [Python Heap Documentation](#python-heap-documentation)
- [Methods](#methods)
  - [heappush](#heappush)
  - [heappop](#heappop)
  - [heappushpop](#heappushpop)
  - [heapify](#heapify)
  - [heapreplace](#heapreplace)
  - [merge](#merge)
  - [nlargest](#nlargest)
  - [nsmallest](#nsmallest)

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
### heappush

```python
heapq.heappush(heap, item)
```
Push the value item onto the heap, maintaining the heap invariant.

```python
>>> heap = [1, 3, 5, 7, 9]
>>> heapq.heappush(heap, 0)
>>> heap
[0, 3, 1, 7, 9, 5]
>>> heapq.heappush(heap, 2)
>>> heap
[0, 3, 1, 7, 9, 5, 2]
>>> heapq.heappush(heap, 8)
>>> heap
[0, 3, 1, 7, 9, 5, 2, 8]
>>> heapq.heappush(heap, 12)
>>> heap
[0, 3, 1, 7, 9, 5, 2, 8, 12]
```

[🔼](#Heapq-documentation)
### heappop

```python
heapq.heappop(heap)
```

Pop and return the smallest item from the heap, maintaining the heap invariant. 
If the heap is empty, IndexError is raised. To access the smallest item without popping it, use heap[0].

```python
>>> heap = [1, 3, 5, 7, 9]
>>> heapq.heappop(heap)
1
>>> heap
[3, 5, 7, 9]
>>> heapq.heappop(heap)
3
>>> heap
[5, 7, 9]
>>> heapq.heappop(heap)
5
>>> heap
[7, 9]
```

[🔼](#Heapq-documentation)
### heappushpop

```python
heapq.heappushpop(heap, item)
```

Push item on the heap, then pop and return the smallest item from the heap. 
The combined action runs more efficiently than heappush() followed by a separate call to heappop().

```python
>>> heap = [1, 3, 5, 7, 9]
>>> heapq.heappushpop(heap, 2)
1
>>> heap
[2, 3, 5, 7, 9]
>>> heapq.heappushpop(heap, 4)
2
>>> heap
[3, 4, 5, 7, 9]
>>> heapq.heappushpop(heap, 6)
3
>>> heap
[4, 6, 5, 7, 9]
```

[🔼](#Heapq-documentation)
### heapify

```python
heapq.heapify(x)
```

Transform list x into a heap, in-place, in linear time.

```python
>>> lst = [5, 3, 8, 1, 2]
>>> heapq.heapify(lst)
>>> lst
[1, 2, 8, 5, 3]
```

[🔼](#Heapq-documentation)
### heapreplace

```python
heapq.heapreplace(heap, item)
```

Pop and return the smallest item from the heap, and also push the new item. The heap size doesn’t change. If the heap is empty, IndexError is raised.

This one step operation is more efficient than a heappop() followed by heappush() and can be more appropriate when using a fixed-size heap. 
The pop/push combination always returns an element from the heap and replaces it with item.

The value returned may be larger than the item added. If that isn’t desired, consider using heappushpop() instead. Its push/pop combination returns the smaller of the two values, leaving the larger value on the heap.

```python
>>> heap = [1, 3, 5, 7, 9]
>>> heapq.heapreplace(heap, 10)
1
>>> heap
[3, 7, 5, 10, 9]
>>> heapq.heapreplace(heap, 0)
3
>>> heap
[0, 7, 5, 10, 9]
>>> heapq.heapreplace(heap, 4)
0
>>> heap
[4, 7, 5, 10, 9]
```

[🔼](#Heapq-documentation)
### merge

```python
iterator = heapq.merge(*iterables, key=None, reverse=False)
```

Merge multiple sorted inputs into a single sorted output (for example, merge timestamped entries from multiple log files). Returns an iterator over the sorted values.

Similar to sorted(itertools.chain(*iterables)) but returns an iterable, does not pull the data into memory all at once, and assumes that each of the input streams is already sorted (smallest to largest).

Has two optional arguments which must be specified as keyword arguments.

key specifies a key function of one argument that is used to extract a comparison key from each input element. The default value is None (compare the elements directly).

reverse is a boolean value. If set to True, then the input elements are merged as if each comparison were reversed. To achieve behavior similar to sorted(itertools.chain(*iterables), reverse=True), all iterables must be sorted from largest to smallest.

```python
# Merge multiple sorted inputs into a single sorted output.
>>> a = [1, 3, 5]
>>> b = [2, 4, 6]
>>> list(heapq.merge(a, b))
[1, 2, 3, 4, 5, 6]
# Example with key and reverse parameters (inputs must be pre-sorted accordingly)
>>> a_desc = [5, 3, 1]
>>> b_desc = [6, 4, 2]
>>> list(heapq.merge(a_desc, b_desc, reverse=True))
[6, 5, 4, 3, 2, 1]
```

[🔼](#Heapq-documentation)
### nlargest

```python
list = heapq.nlargest(n, iterable, key=None)
```

Return a list with the n largest elements from the dataset defined by iterable. 
key, if provided, specifies a function of one argument that is used to extract a comparison key from each element in iterable 
(for example, key=str.lower). Equivalent to: sorted(iterable, key=key, reverse=True)[:n].

```python
>>> data = [1, 8, 2, 23, 7, -4, 18, 23, 42, 37, 2]
>>> heapq.nlargest(3, data)
[42, 37, 23]
```

[🔼](#Heapq-documentation)
### nsmallest

```python
list = heapq.nsmallest(n, iterable, key=None)
```

Return a list with the n smallest elements from the dataset defined by iterable. 
key, if provided, specifies a function of one argument that is used to extract a comparison key from each element in iterable 
(for example, key=str.lower). Equivalent to: sorted(iterable, key=key)[:n].

```python
>>> data = [1, 8, 2, 23, 7, -4, 18, 23, 42, 37, 2]
>>> heapq.nsmallest(3, data)
[-4, 1, 2]
```

