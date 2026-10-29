# CMPS 6610 Problem Set 04
## Answers

**Name:** $\underline{\hspace{1in}\text{Rob Hartley}\hspace{1in}}$


Place all written answers from `problemset-04.md` here for easier grading.




- **1d.**

File | Fixed-Length Coding | Huffman Coding | Huffman vs. Fixed-Length
----------------------------------------------------------------------
f1.txt    |      $1340$               |     $826$           |  $0.6164$
alice29.txt    |         $1039367$            |         $676374$       |  $0.6508$
asyoulik.txt    |         $876253$            |        $606448$        |  $0.6921$
grammar.lsp    |            $26047$         |     $17356$           |  $0.6663$
fields.c    |            $78050$         |        $56206$        |  $0.7201$

The pattern that emerges is that:  
Huffman cost $\leq$ Fixed-Length cost. This is because Huffman coding achieves a lower encoding cost relative to Fixed Length by assigning shorter binary codes to more frequently used characters and longer codes to less fequently used characters. The more uneven the distribution between frequencies of the characters being used in a document, the greater the Huffman cost reduction we'd expect to see. Our samples reflect that, and show a cost recution range of roughly 28% - 38%.  

- **1e.**  
When all characters in alphabet $\sum$ have the same frequency, Huffman coding produces either a balanced or near balanced tree.  
Let characters $c = |\sum|$ and tree height ceiling $h = \lceil\log_2c\rceil$. The codeword length for each character in the tree will be either $h$ or $h - 1$ with $2^h - c$ characters using $h - 1$ bits and $2c - 2^h$ characters using $h$ bits. From this information, we can determine average number of bits per character $A_b$ with this equation:  

    $A_b = \frac{(2^h - c)(h - 1) + (2c - 2^h)(h)}{c}$  
      
    $A_b = \frac{2^hh -2^h - ch + c + 2ch -2^hh}{c}$  

    $A_b = \frac{-2^h + c + ch}{c}$  

    $A_b = h + 1 - \frac{2^h}{c}$  

    If we have $n$ total number of characters in our document and the frequency of each distinct charactor is the same, then the Huffman coding cost would be:  

    $\boxed{\text{Huffman Cost} = n \cdot \left(h + 1 - \frac{2^h}{c}\right)}$  

    This equation applies to all documents where each distinct character occurs with equal frequency. The Huffman coding cost will be consistent across documents with the same total number of characters $n$ and the same number of distinct characters $c$. However, the coding cost may change if either $n$ or $c$ changes.






- **2a.** Construct a binary min-heap algorithm  

    This algorithm would be a bottom up algorithm, starting at the bottom right internal node (not the leaves) and working it's way up the tree. For each node, the node value is compared to its children. If the parent value isn't already the lowest value, it is swapped with the lowest child value, which becomes the new parent. Because the bottom right internal node will also have the highest index value for an inernal node in the list, and all other index values below it will also represent internal nodes, we then decrement the index and repeat the process until we reach the root node. The min-heap is now built.  

    ```text
    def sift_down(A, i, n):
        while 2*i + 1 < n:
            left = 2*i + 1
            right = 2*i + 2
            smallest = left

            if right < n and A[right] < A[left]:
                smallest = right

            if A[i] <= A[smallest]:
                break

            A[i], A[smallest] = A[smallest], A[i]
            i = smallest


    def build_min_heap(A):
        n = len(A)

        for i in range(n // 2 - 1, -1, -1):
            sift_down(A, i, n)
    ```
    buildMinHeap:  
    This method is a loop that executes $\lfloor\frac{n}{2}\rfloor$ times, doing constant work each time, excluding the call to siftDown.
    $W_{BH}(n) = \sum_{i=1}^{\lfloor\frac{n}{2}\rfloor} \Theta(1)$  
    $W_{BH}(n) = \lfloor\frac{n}{2}\rfloor \cdot \Theta(1)$  
    $W_{BH}(n) \in \Theta(n)$  

    siftDown:  
    Each node can move downward by no more than its height $h$ in the tree. Each move costs $\Theta(1)$. So each node requires at most $O(h + 1)$ work.
    There are at most $\lceil\frac{n}{2^{h + 1}}\rceil$ nodes at height $h$. Therefore:  

    $W_{SD} = O\left(n\sum_{h=0}^{\lfloor\log_2 n\rfloor}\frac{h+1}{2^{h+1}}\right)$  
     $\sum_{h=0}^{\lfloor\log_2 n\rfloor}\frac{h+1}{2^{h+1}} \leq \sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}}$  
    $\sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} = \frac{1}{2^1} + \frac{2}{2^2} + \frac{3}{2^3} + \frac{4}{2^4} + \dots = \frac{1}{2} + \frac{2}{4} + \frac{3}{8} + \frac{4}{16} + \dots$  
    $\left(\frac{1}{2}\right) \cdot \sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} = \left(\frac{1}{2}\right) \cdot \left(\frac{1}{2^1} + \frac{2}{2^2} + \frac{3}{2^3} + \frac{4}{2^4} + \dots\right) = \frac{1}{4} + \frac{2}{8} + \frac{3}{16} + \frac{4}{32} + \dots$  
    $\sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} - \left(\frac{1}{2}\right) \cdot \sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} = \frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \frac{1}{16} + \dots = \sum_{h=0}^{\infty}(\frac{1}{2})^{(h+1)}$

    Infinite Geometric Series  
    $\sum_{i=0}^{\infty}ar^k = \frac{a}{1 - r}, |r| < 1$  
    $\sum_{h=0}^{\infty}(\frac{1}{2})^{(h+1)},  a = \frac{1}{2}, r = \frac{1}{2}$  
    $\sum_{h=0}^{\infty}(\frac{1}{2})^{(h+1)} = \frac{1/2}{1 - 1/2} = 1$  

    Combine      
    $\left(\frac{1}{2}\right) \cdot \sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} = 1$  
    $\sum_{h=0}^{\infty}\frac{h+1}{2^{h+1}} = 2$  
    $W_{SD} = O(2n)$  
    $W_{SD} \in O(n)$  

    $W_{total} = W_{BH}(n) + W_{SD}$  
    $W_{total} = \Theta(n) + O(n)$  

    $\boxed{W_{total} \in \Theta(n)}$


- **2b.** Span of your algorithm  
There is no parallelism in the algorithm. The buildHeap loop executes sequentially, as do all the operations in siftDown. Span = Work.  
$\boxed{S_{total} \in \Theta(n)}$




- **3a.** Greedy algorithm for making change  
```text
    def greedyCoins(N, k):
    coins = []
    remaining = N

    for i in range(k, -1, -1):
        denomination = 2 ** i
        count = remaining // denomination
        remaining = remaining % denomination
        coins.append((denomination, count))

    return coins  
```



- **3b.** Optimality proof  
The optimal solution for this problem is to return a combination of the minimum total number of coins that will 




- **3c.** Work and span of your algorithm



- **4a.** Fortuito counter example proof



- **4b.** Optimal substructure property




- **4c.** Fortuito dynamic programming algorithm




- **5a.** Weighted task selection: Optimal substructure?



- **5b.** Does the greedy choice property hold?




- **5c.** Dynamic programming algorithm for Weighted Task Selection
