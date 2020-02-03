# Data Structure

## Tree
A tree starts from a node called *root*. Each node can have multiple children, but only one parent (besides the root).

### Heap
Heap is a binary tree with special rules (ex. value in the parent node >= value in the child node would be the rule for *max heap*).

Example: priority queue would be a max heap.
When taking a value out of a proiority queue, the hightest value will always be at the root. After taking out the current max value out, the root value will be empty. From the deepest rank of the child nodes, a value will be selected to put at the root. Since the current root value is not the highest value, it will swap with the child node with the highest value. The value will bubble down all the way until its value is no more smaller than the child nodes. This way instead of sorting through the whole structure, only a small portion of nodes are sorted, and the max value will always be at the root.
Inserting a new value or node is similar. The value will be insert at the max depth. Then the new value will be compared with its parent and bubble up until it is no more bigger than its parent.
The runtime for heap is O(log N), meaning when doubling the size of the data, only 1 more operation is needed.

### Binary Search Tree
For a BST, the value in the child node on the left is always <= the parent value, and the value in the right child node is always >= the parent value. The tree is prioritize for searching, and the runtime is O(log N).


[Back](../../README.md)
