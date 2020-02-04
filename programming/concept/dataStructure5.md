# Data Structure

## Memory
CPU Registers | CPU Caches | RAM | Hard Disk / SSD | Network
The further left, the closer it is to the CPU, the faster user have access to the data.

If the data is not in CPU Caches, the system will have to go to RAM or HD/SSD to find the data. This is called *cache miss*, which is important if it happens too many times in 1 operation.

## B-Tree
B-Tree is a search optimized to reduce cache misses.

In a B-Tree, the root contains an array holding multiple sorted data. When looking for a data, we compare the data with the data inside root, find what is the first value that is larger than the datat we are looking for (if the array is sorted from small to large). Than we go to the child array containing the inbetween segment of the values.

Example:
root: `[8, 14, 27, 39]`
child: `[1, 7]`, `[10, 13]`, `[22, 25]`, `[28, 31]`

Example for inserting data into a 2-3 B-Tree (each array can only contain 2 data and 3 child):
Starts by inserting data into a single node in the furtherest depth (called leaf).
If the array is full, look for siblings next to the current node and see if there's space.
If there's no space or no siblings, split the array into 2 and shuffle the data so the middle one is in the parent node.
If the child branches are full for the parent, split a level above and create another node directly below root that is the parent for all the current tree.

Similar operation is done in the opposite for deleting data. Note that restructuring is avoided unless it is absolutely necessary.
Also parent.length will have to = number of child nodes + 1.

Used when constant access HD/SSD is required, such as indexing database or files. The advantage of B-Tree over hash table is that data B-Tree is already sorted.

## Graph
Graph is a combination of nodes and relationships. It can be a combination of other data structures (linked list, trees, etc) or simply total chaos.

Different strategy: Breadth First or Depth First -
BFS: checks all the connections in one single node before going to another node.
DFS: going to one node at a time.

Dijkstra's algorithm is an algorith used to find the shortest path between nodes.

[Back](../../README.md)
