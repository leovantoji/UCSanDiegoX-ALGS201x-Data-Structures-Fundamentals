# UCSanDiegoX-ALGS201x-Data-Structures-Fundamentals

## Course Summary
### Array: 
- Contiguous are of memory consisting of equal-sized elements indexed by contiguous integers.
- Constant time access to any element.
- *O(n)* time to add/remove at any arbitrary location.
- *O(1)* time to add/remove at the end of the array.

### Linked List:
- Node contains key and next pointer.
- List API:

  |Function|Usage|Run time (Singly-liked list)|Run time (Doubly-liked list)|
  |---|---|:---:|:---:|
  |PushFront(key)|add to front|*O(1)*|*O(1)*|
  |Key TopFront()|return front item|*O(1)*|*O(1)*|
  |PopFront()|remove front item|*O(1)*|*O(1)*|
  |PushBack(Key)|add to back|No tail: *O(n)* With tail: *O(1)*|*O(1)*|
  |Key TopBack()|return back item|No tail: *O(n)* With tail: *O(1)*|*O(1)*|
  |PopBack()|remove back item|*O(n)*|*O(1)*|
  |Boolean Find(Key)|is key in list?|*O(n)*|*O(n)*|
  |Erase(Key)|remove key from list|*O(n)*|*O(n)*|
  |Boolean Empty()|is list empty?|*O(1)*|*O(1)*|
  |AddBefore(Node, Key)|add key before node|*O(n)*|*O(1)*|
  |AddAfter(Node, Key)|add key after node|*O(1)*|*O(1)*|

### Stack: 
- Abstract data type with the following operations:

  |Function|Usage|Run time|
  |---|---|:---:|
  |Push(Key)|add key to collection|*O(1)*|
  |Key Top()|return most recently-added key|*O(1)*|
  |Key Pop()|remove and return most recently-added key|*O(1)*|
  |Boolean Empty()|is stack empty?|*O(1)*|
- LIFO.
- Implemented with array or linked-list:
  - Linked-list has a fixed amount of overhead (additional pointer for every new element).
  - Maximum size for array, and no maximum size for linked-list.

### Queue:
- Abstract data type with the following operations:
  
  |Function|Usage|Run time|
  |---|---|:---:|
  |Enqueue(Key)|add key to collection|*O(1)*|
  |Key Dequeue()|return least recently-added key|*O(1)*|
  |Boolean Empty()|is queue empty?|*O(1)*|
- FIFO.
- Implemented with array or linked list:
  - Linked List: Enqueue uses List.PushBack. Dequeue uses List.TopFront and List.PopFront. Empty uses List.Empty.
  - Array: To make sure read and write are separate and distint, at least one element can't be written to.

### Tree: 
- Empty or a node with a key or a list of child trees.
- Node:
  - Key.
  - Children: list of children nodes.
  - Parent (Optional).
- Binary Search Tree:
  - At most 2 children for each node.
  - The value of the root node is greater than or equal to all nodes of its left child.
  - The value of the root node is less than or equal to all nodes of its right child.
- Tree Traversal:
  - Depth First Search (DFS):
    - InOderTraversal: Left Node Right.
    - PreOrderTraversal: Node Left Right.
    - PostOrderTraversal: Left Right Node.
  - Breadth First Search (BFS):
    - LevelTraversal.

### Dynamic Array (Resizable Array):
- Store a pointer to a dynamically allocated array, and replace it with a newly-allocated array as needed.
- Abstract data type with the following operations (at a minimum):
  
  |Function|Usage|Run time|
  |---|---|:---:|
  |Get(*i*)|return element at location *i*|*O(1)*|
  |Set(*i,val*)|set element *i* to *val*|*O(1)*|
  |PushBack(*val*)|add *val* to the end|*O(n)*|
  |Remove(*i*)|remove element *i*|*O(n)*|
  |Size()|return size of the array|*O(1)*|
- Amortised Analysis:
  - Aggregate method:
    - Amortised cost: Given a sequence of *n* operations, the amortised cost is: Cost(*n* operations)/n.
    - Amortised cost is *O(1)*.
  - Banker's method:
    - Charge extra for each cheap operation.
    - Save the extra charge as tokens in your data structure (conceptually).
    - Use the tokens to pay for the expensive operations.
  - Physicist's method:
    - Define a potential function, which maps states of the data structures to integers.
    - Amortised cost *c<sub>t</sub>* (for operation *t*) is sum of the true cost and the change in potential.
    - Choose the potential function such that if *c<sub>t</sub>* is small, the potential increases, and if *c<sub>t</sub>* is large, the potential decreases by the same scale.

### Priority Queue:
- Abstract data type with the following operations:
  
  |Function|Usage|
  |---|---|
  |Insert(*p*)|add a new element with priority *p*|
  |ExtractMax()|extract an element with maximum priority|
  |Remove(*it*)|remove an element pointed by an iterator *it*|
  |GetMax()|return an element with maximum priority w/o changing the set of elements|
  |ChangePriority(*it*,*p*)|change the priority of an element pointed by *it* to *p*|    
- Built-in implementations:
  - C++: priority_queue
  - Java: PriorityQueue
  - Python: heapq
- Naive implementation:
  - Unsorted Array/Doubly-linked List: *O(1)* for Insert(e), *O(n)* for ExtractMax().
  - Sorted Array: *O(n)* for Insert(e), *O(1)* for ExtractMax().
  - Sorted List: *O(n)* for Insert(e), *O(1)* for ExtractMax().
