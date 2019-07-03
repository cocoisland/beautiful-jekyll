---
title: Can't judge a program by its cover.
subtitle: Algorithm and data structure are the unseen essential parts that make a good performing application.
image: /img/algorithm/codeIcon.jpg
---
This article consisted of an assortment of useful algorithm and data structure concept that are important for all critical applications.

### Memory Constraint problem
Say on an embedded computer with very limited RAM, memory is extremely constrained and you are only allowed to store names in arrays. The challenge is to optimize a O(n^2) program, [names.py](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/blob/master/names/names.py) . 

Since dictionary or hash table allowed fastest access time O(1) and array n or O(n) space complexities, I implemented dictionary data structure to solve the problem with O(1) time and O(n) space complexities in [namesDict.py](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/blob/master/names/nameDict.py)

[Full memory constraint working directory here](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/tree/master/names)

### Ring buffer to storing logs and history information.
A ring buffer is a non-growable buffer with a fixed size. When the ring buffer is full and a new element is inserted, the oldest element in the ring buffer is overwritten with the newest element. This kind of data structure is very useful for use cases such as storing logs and history information, where you typically want to store information up until it reaches a certain age, after which you don't care about it anymore and don't mind seeing it overwritten by newer data.

Efficient fast access time complexities and protection for buffer overflow, are always important for buffer implementation. With a marker variable, I implemented my [Ring buffer solution here](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/blob/master/ring_buffer/ring_buffer.py) with O(1) access time complexities.

### self-maintenance Max Heap for fast data access
Max Heap is a special heap data structure where the largest item value of the heap always automatically floated to the top. The idea is to enable the largest item value to be accessed in fastest O(1) time complexity. When the top largest item value is popped from the heap, the next largest item value will float to its top place. When a new item value is pushed onto the heap, the new item value will sift down to its proper order place.

[self-maintenance Max Heap solution here](https://github.com/cocoisland/Data-Structures/blob/master/heap/max_heap.py)

### Cache


### Graph

