## Programming Assignment 1: Basic Data Structures
### 1.1. Check brackets in the code
**Task:** Your friend is making a text editor for programmers. He is currently working on a feature that will find errors in the usage of different types of brackets. Code can contain any brackets from the set []{}(), where the opening brackets are [,{, and ( and the closing brackets corresponding to them are ],}, and ). For convenience, the text editor should not only inform the user that there is an error in the usage of brackets, but also point to the exact place in the code with the problematic bracket. First priority is to find the first unmatched closing bracket which either doesn’t have an opening bracket before it, like ] in ](), or closes the wrong opening bracket, like } in ()[}. If there are no such mistakes, then it should find the first unmatched opening bracket without the corresponding closing bracket after it, like ( in {}([]. If there are no mistakes, text editor should inform the user that the usage of brackets is correct. Apart from the brackets, code can contain big and small latin letters, digits and punctuation marks. More formally, all brackets in the code should be divided into pairs of matching brackets, such that in each pair the opening bracket goes before the closing bracket, and for any two pairs of brackets either one of them is nested inside another one as in (foo[bar]) or they are separate as in f(a,b)-g[c]. The bracket [ corresponds to the bracket ], { corresponds to }, and ( corresponds to ).\
**Input Format:** Input contains one string *S* which consists of big and small latin letters, digits, punctuation marks and brackets from the set []{}().\
**Constraints:** *0 ≤ len(S) ≤ 10<sup>5</sup>*.\
**Output Format:** If the code in *S* uses brackets correctly, output “Success" (without the quotes). Otherwise, output the 1-based index of the first unmatched closing bracket, and if there are no unmatched closing brackets, output the 1-based index of the first unmatched opening bracket.\
**Memory Limit:** *512*MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|1|1|1|1|3|3|

```python

```

### 1.2. Compute Tree Height
**Task:** You are given a description of a rooted tree. Your task is to compute and output its height. Recall that the height of a (rooted) tree is the maximum depth of a node, or the maximum distance from a leaf to the root. You are given an arbitrary tree, not necessarily a binary tree.\
**Input Format:** The first line contains the number of nodes *n*. The second line contains 𝑛 integer numbers from *−1* to *n − 1* — parents of nodes. If the *i<sup>th</sup>* one of them (*0 ≤ i ≤ n − 1*) is *−1*, node *i* is the root, otherwise it’s 0-based index of the parent of *i<sup>th</sup>* node. It is guaranteed that there is exactly one root. It is guaranteed that the input represents a tree.\
**Constraints:** *0 ≤ n ≤ 10<sup>5</sup>*.\
**Output Format:** Output the height of the tree.\
**Memory Limit:** *512*MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|1|1|6|3|3|3|

```python

```

### 1.3. Network packet processing simulation
**Task:** You are given a description of a rooted tree. Your task is to compute and output its height. Recall that the height of a (rooted) tree is the maximum depth of a node, or the maximum distance from a leaf to the root. You are given an arbitrary tree, not necessarily a binary tree.\
**Input Format:** The first line contains the number of nodes *n*. The second line contains 𝑛 integer numbers from *−1* to *n − 1* — parents of nodes. If the *i<sup>th</sup>* one of them (*0 ≤ i ≤ n − 1*) is *−1*, node *i* is the root, otherwise it’s 0-based index of the parent of *i<sup>th</sup>* node. It is guaranteed that there is exactly one root. It is guaranteed that the input represents a tree.\
**Constraints:** All the numbers in the input are integers. *1 ≤ S ≤ 10<sup>5</sup>*; *0 ≤ n ≤ 10<sup>5</sup>*; *0 ≤ A<sup>i</sup> ≤ 10<sup>6</sup>*; *0 ≤ P<sup>i</sup> ≤ 10<sup>3</sup>*; *A<sup>i</sup> ≤ A<sup>i+1</sup>* for *1 ≤ i ≤ n − 1*.\
**Output Format:** For each packet output either the moment of time (in milliseconds) when the processor began processing it or *−1* if the packet was dropped (output the answers for the packets in the same order as the packets are given in the input).\
**Memory Limit:** *512*MB.\
**Time Limits:**

|Language|C|C++|Java|Python|JavaScript|Scala|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Time (sec)|2|2|6|8|6|6|

```python

```
