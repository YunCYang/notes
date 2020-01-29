# Data Structure

## Linked List

Linked list is not continuous data (as the case in array). Linked list consists of various nodes, each consist of 2 properties: a *value* containing actual value, and a *next* pointing to the address of the next node. The *next* property of the last element of the list will point to `null` (often actually means 0x0 in the machine).

A separate start pointer will points to the first element of the list, sometimes a tail pointer points to the last element of the list.

Example for singly linked list:
```
head: 0x59;

first-elemet: {
  value: 12,
  next: 0x37
};

second-element: {
  value: 'q',
  next: 0x15
}

last-element: {
  value: true,
  next: null
}

tail: 0x15;
```

A doubly linked list would contains a *prev* property to keep track of the data previous of the current node. Other variations of linked list also exists.

The list isn't continuous, so when adding data, there's no need to reallocate memory. New node can be stored anywhere. Another difference from the array is that each node inside a linked list can store any data type or size of data.

Singly Linked List (with a tail pointer):
- Read
  - Next / Prev value         O(1) / O(N)
  - Get value by key          O(N)
  - Search by value           O(N)
- Insert
  - Append / Prepend          O(1)
  - Arbitrary insert with ref O(1)
- Delete
  - Delete first / last value O(1) / O(N)
  - Arbitrary delete with ref O(1)
- Update
  - Replace value with ref    O(1)
  - Swap                      O(1) (use multiple temp to store *next* and update)
- Bulk Operations

Linked list is good for a list of big objects that needs to be keep tracked of, as it's difficult to allocate memory for a list of big objects. Also good when there a frequent need to constantly adding, deleting or manipulating data inside the list.

## Circular Linked List

Instead of pointing to null, the *next* property instead points to the head node. The *head* and *tail* pointer is replace with a *curr* pointing to the current node.

Greatly minimized the operations as there's no more first or last node.

Similar idea to the event loop, as the user is constantly going through all the nodes in the list checking each element.

[Back](../../README.md)
