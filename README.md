# UCSanDiegoX-ALGS201x-Data-Structures-Fundamentals

## Course Summary
- Array:
  - Contiguous are of memory consisting of equal-sized elements indexed by contiguous integers.
  - Constant time access to any element.
  - *O(n)* time to add/remove at any arbitrary location.
  - *O(1)* time to add/remove at the end of the array.
- Linked List:
  - Node contains key and next pointer.
  - List API:
  
    |Function|Usage|Run time (Singly-liked list)|Run time (Doubly-liked list)|
    |---|---|---|---|
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
- Stack: Abstract data type with the following operations:
  - Function|Usage|Run time|
    |---|---|---|
    |Push(Key)|add key to collection|*O(1)*|
    |Key Top()|return most recently-added key|*O(1)*|
    |Key Pop()|remove and return most recently-added key|*O(1)*|
    |Empty()|is stack empty?|*O(1)*|
  - LIFO queues
  - Stacks can be implemented with array or linked-list:
    - Linked-list has a fixed amount of overhead (additional pointer for every new element).
    - Maximum size for array, and no maximum size for linked-list.
