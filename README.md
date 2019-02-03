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
