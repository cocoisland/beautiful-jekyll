---
title: Can't judge a program by its cover.
subtitle: Algorithm and data structure are the unseen essential parts that make a good performing application.
image: /img/algorithm/codeIcon.jpg
---
This article consisted of an assortment of useful algorithm and data structure concept that are important for all critical applications.

### Memory Constraint problem
Say on an embedded computer with very limited RAM, memory is extremely constrained and you are only allowed to store names in arrays. The challenge is to find all duplicate from two data sets. Dictionary or hash table allowed fastest access time O(1) and array n or O(n) space complexities. Dictionary data structure was implemented to solve the problem with O(1) time and O(n) space complexities in [namesDict.py](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/blob/master/names/nameDict.py)

### Hash table or Dictionary provided best access performance.
Since computing is expensive and memory cheap, Hashtable or Dictionary offers viable solutions to problem situations which required fast access time given acceptable memory requirement. 

Given a package with a weight limit and a list weights of item weights, a function was implemented to finds two items whose sum of weights equals the weight limit limit.

Each weight in the input list was stored as hash table key and each weight list index was stored as hash table value. The solution can then solved by checking whether the hash table contains an entry for the difference of limit minue weight.

[Fitting items by weights in a package](https://github.com/cocoisland/Sprint-Challenge--Hash-BC/blob/master/hashtables/ex1/ex1.py), was solved in O(n) time.

### Ring buffer to storing logs and history information.
A ring buffer is a non-growable buffer with a fixed size. When the ring buffer is full and a new element is inserted, the oldest element in the ring buffer is overwritten with the newest element. This kind of data structure is very useful for use cases such as storing logs and history information, where you typically want to store information up until it reaches a certain age, after which you don't care about it anymore and don't mind seeing it overwritten by newer data.

Efficient fast access time complexities and protection for buffer overflow, are always important for buffer implementation. With a marker variable, I implemented my [Ring buffer solution here](https://github.com/cocoisland/Sprint-Challenge--Data-Structures-Python/blob/master/ring_buffer/ring_buffer.py) with O(1) access time complexities.

### self-maintenance Max Heap for fast data access
Max Heap is a special Heap data structure based on tree graph where largest value items of the Heap are always available in fastest O(1) time complexity. When new items are added to the tree, the new items are moved to its appropriate value order in the tree. When the largest value item is removed, the second largest item in the heap tree will be placed in its root node.

[self-maintenance Max Heap solution here](https://github.com/cocoisland/Data-Structures/blob/tony-tia/heap/max_heap.py)

#### FILO Max Stack for fast data access
Max Stack is a special Stack data structure where largest value items on the Stack are always available in fastest O(1) time complexity. Unlike Heap, items that are pushed and popped off the Stack, are based on first-in-last-out (FILO).

[FILO Max Stack](https://github.com/cocoisland/Algorithms/blob/tony-tia/misc/maxStack.py)

### Graph
Graphs are collections of related data. Hence they can be used to solve not only traditional tree problems, but any connected or related data problems.

Word Ladder is a problem where given two words (beginWord and endWord), and a dictionary's word list, find the length of shortest transformation sequence from beginWord to endWord, such that: 
1. Only one letter can be changed at a time.
2. Each transformed word must exist in the word list. Note that beginWord is not a transformed word.

[Word Ladder solution here](https://github.com/cocoisland/Graphs/blob/master/projects/graph_problem/wordLadder.py) is a clever ways to make use of graph basic queue or stack structure to loop through related objects or nodes. The graph adaptation to solving word ladder problem, is to build a dictionary of all alphabet permutation letters of dictionary words. The space complexity for such dictionary words permutation will be O(n * 26), for 26 alphabet letters where n is the length of dictionary words.

Finding number of Island in a 2x2 binary matrix, where a group of connected 1s formed an island, is another problem that can be solved using a graph methodology. Using graph queue or stack data structure to process connected 1s, the problem solving function of the program, is to define the border of the islands in the matrix.

[Finding Island solution here](https://github.com/cocoisland/Graphs/blob/master/projects/graph_problem/island.py)


