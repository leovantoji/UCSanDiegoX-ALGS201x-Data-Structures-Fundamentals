## Programming Assignment 1: Basic Data Structures
### 1.1. Check brackets in the code
**Task:** Your friend is making a text editor for programmers. He is currently working on a feature that will find errors in the usage of different types of brackets. Code can contain any brackets from the set []{}(), where the opening brackets are [,{, and ( and the closing brackets corresponding to them are ],}, and ). For convenience, the text editor should not only inform the user that there is an error in the usage of brackets, but also point to the exact place in the code with the problematic bracket. First priority is to find the first unmatched closing bracket which either doesn’t have an opening bracket before it, like ] in ](), or closes the wrong opening bracket, like } in ()[}. If there are no such mistakes, then it should find the first unmatched opening bracket without the corresponding closing bracket after it, like ( in {}([]. If there are no mistakes, text editor should inform the user that the usage of brackets is correct. Apart from the brackets, code can contain big and small latin letters, digits and punctuation marks. More formally, all brackets in the code should be divided into pairs of matching brackets, such that in each pair the opening bracket goes before the closing bracket, and for any two pairs of brackets either one of them is nested inside another one as in (foo[bar]) or they are separate as in f(a,b)-g[c]. The bracket [ corresponds to the bracket ], { corresponds to }, and ( corresponds to ).\
**Input Format:** Input contains one string *S* which consists of big and small latin letters, digits, punctuation marks and brackets from the set []{}().\
**Constraints:** *0 ≤ len(S) ≤ 10<sup>5</sup>*.\
**Output Format:** If the code in *S* uses brackets correctly, output “Success" (without the quotes). Otherwise, output the 1-based index of the first unmatched closing bracket, and if there are no unmatched closing brackets, output the 1-based index of the first unmatched opening bracket.\
**Memory Limit:** *512* MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|1|1|1|1|3|3|

```python
from collections import namedtuple

Bracket = namedtuple("Bracket", ["char", "position"])

def are_matching(left, right):
    return (left + right) in ["()", "[]", "{}"]

def find_mismatch(text):
    opening_brackets_stack = []
    for i, next in enumerate(text):
        if next in "([{":
            # Process opening bracket
            opening_brackets_stack.append(Bracket(char = next, position = (i+1)))

        if next in ")]}":
            # Process closing bracket
            n = len(opening_brackets_stack)
            
            if n != 0 and are_matching(opening_brackets_stack[n-1].char, next):
                opening_brackets_stack.pop(n-1)
            else:    
                return (i+1)
    
    n = len(opening_brackets_stack)
    
    if n == 0:
        return 'Success'
    else:
        return opening_brackets_stack[n-1].position
```

### 1.2. Compute Tree Height
**Task:** You are given a description of a rooted tree. Your task is to compute and output its height. Recall that the height of a (rooted) tree is the maximum depth of a node, or the maximum distance from a leaf to the root. You are given an arbitrary tree, not necessarily a binary tree.\
**Input Format:** The first line contains the number of nodes *n*. The second line contains 𝑛 integer numbers from *−1* to *n − 1* — parents of nodes. If the *i<sup>th</sup>* one of them (*0 ≤ i ≤ n − 1*) is *−1*, node *i* is the root, otherwise it’s 0-based index of the parent of *i<sup>th</sup>* node. It is guaranteed that there is exactly one root. It is guaranteed that the input represents a tree.\
**Constraints:** *0 ≤ n ≤ 10<sup>5</sup>*.\
**Output Format:** Output the height of the tree.\
**Memory Limit:** *512* MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|1|1|6|3|3|3|

Method 1:
```python
import queue

class Node:
    def __init__(self, index):
        self.index = index
        self.children = []
    
    def addChild(self, child):
        self.children.append(child)
    
def compute_height(n, parents):
    nodes = [Node(i) for i in range(n)]
    
    for i in range(n):
        if parents[i] == -1:
            root = nodes[i]
        else:
            nodes[parents[i]].addChild(nodes[i])
    
    q = queue.Queue()
    q.put(root)
    height = 0
    
    while (not q.empty()):
        size = q.qsize()
        if size > 0:
            height += 1
        for i in range(size):
            item = q.get()
            for i in item.children:
                q.put(i)
    
    return height
```

Method 2:
```python
from collections import namedtuple

Node = namedtuple("Node", ["key", "children"])
    
def compute_height(n, parents):
    nodes = [Node(key = i, children = []) for i in range(n)]
    
    for i in range(n):
        if parents[i] == -1:
            root = nodes[i]
        else:
            nodes[parents[i]].children.append(nodes[i])
    
    def height(root):
        if len(root.children) == 0:
            return 0
        
        max_height = 1
        
        for child in root.children:
            ht = height(child)
            if ht > max_height:
                max_height = ht
    
        return max_height + 1
    
    return height(root)
```

### 1.3. Network packet processing simulation
**Task:** You are given a series of incoming network packets, and your task is to simulate their processing. Packets arrive in some order. For each packet number *i*, you know the time when it arrived *A<sub>i</sub>* and the time it takes the processor to process it *P<sub>i</sub>* (both in milliseconds). There is only one processor, and it processes the incoming packets in the order of their arrival. If the processor started to process some packet, it doesn’t interrupt or stop until it finishes the processing of this packet, and the processing of packet *i* takes exactly *P<sub>i</sub>* milliseconds. The computer processing the packets has a network buffer of fixed size *S*. When packets arrive, they are stored in the buffer before being processed. However, if the buffer is full when a packet arrives (there are *S* packets which have arrived before this packet, and the computer hasn’t finished processing any of them), it is dropped and won’t be processed at all. If several packets arrive at the same time, they are first all stored in the buffer (some of them may be dropped because of that — those which are described later in the input). The computer processes the packets in the order of their arrival, and it starts processing the next available packet from the buffer as soon as it finishes processing the previous one. If at some point the computer is not busy, and there are no packets in the buffer, the computer just waits for the next packet to arrive. Note that a packet leaves the buffer and frees the space in the buffer as soon as the computer finishes processing it.\
**Input Format:** The first line of the input contains the size *S* of the buffer and the number *n* of incoming network packets. Each of the next *n* lines contains two numbers. *i<sup>th</sup>* line contains the time of arrival *A<sub>i</sub>* and the processing time *P<sub>i</sub>* (both in milliseconds) of the *i<sup>th</sup>* packet. It is guaranteed that the sequence of arrival times is non-decreasing (however, it can contain the exact same times of arrival in milliseconds — in this case the packet which is earlier in the input is considered to have arrived earlier).\
**Constraints:** All the numbers in the input are integers. *1 ≤ S ≤ 10<sup>5</sup>*; *0 ≤ n ≤ 10<sup>5</sup>*; *0 ≤ A<sub>i</sub> ≤ 10<sup>6</sup>*; *0 ≤ P<sub>i</sub> ≤ 10<sup>3</sup>*; *A<sub>i</sub> ≤ A<sub>i+1</sub>* for *1 ≤ i ≤ n − 1*.\
**Output Format:** For each packet output either the moment of time (in milliseconds) when the processor began processing it or *−1* if the packet was dropped (output the answers for the packets in the same order as the packets are given in the input).\
**Memory Limit:** *512* MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|2|2|6|8|6|6|

```python
# python3
from collections import namedtuple

Request = namedtuple("Request", ["arrived_at", "time_to_process"])
Response = namedtuple("Response", ["was_dropped", "started_at"])

class Buffer:
    def __init__(self, size):
        self.size = size
        self.finish_time = []
        
    def process(self, request): 
        # release finished packets
        def findIndex(a,key):
            if len(a) == 0:
                return -1

            left, right = 0, len(a) - 1

            rValue = -1
            while left <= right:        
                mid = (left + right) // 2
                if a[mid] > key:
                    right = mid - 1
                else:
                    rValue = mid
                    left = mid + 1

            return rValue
        
        countPackets = findIndex(self.finish_time, request.arrived_at)
        
        if countPackets != -1:
            self.size += (countPackets + 1)      
            if countPackets == 0:
                self.finish_time.pop(0)
            else:
                self.finish_time = self.finish_time[(countPackets+1):]
        
        # check if buffer is full or not
        if self.size >= 1:
            # store packet into buffer
            self.size -= 1
            # initiate request
            self.request = request
                
            # identify latest packet's finish time
            n = len(self.finish_time)
            
            if n == 0:
                st = request.arrived_at
            else:
                st = max(self.finish_time[n-1], request.arrived_at)    
            
            ft = st + request.time_to_process
            
            # find where to add ft to make sure finish_time is in increasing order
            i = findIndex(self.finish_time,ft)
            if i == -1:
                self.finish_time.insert(0,ft)
            else:
                self.finish_time.insert(i+1,ft)
            
            return Response(False, st)
        
        return Response(True, -1)

def process_requests(requests, buffer):
    responses = []
    for request in requests:
        responses.append(buffer.process(request))
    return responses

def main():
    buffer_size, n_requests = map(int, input().split())
    requests = []
    for _ in range(n_requests):
        arrived_at, time_to_process = map(int, input().split())
        requests.append(Request(arrived_at, time_to_process))

    buffer = Buffer(buffer_size)
    responses = process_requests(requests, buffer)

    for response in responses:
        print(response.started_at if not response.was_dropped else -1)

if __name__ == "__main__":
    main()
```
