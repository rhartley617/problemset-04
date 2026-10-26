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




- **2b.** Span of your algorithm




- **3a.** Greedy algorithm for making change



- **3b.** Optimality proof




- **3c.** Work and span of your algorithm



- **4a.** Fortuito counter example proof



- **4b.** Optimal substructure property




- **4c.** Fortuito dynamic programming algorithm




- **5a.** Weighted task selection: Optimal substructure?



- **5b.** Does the greedy choice property hold?




- **5c.** Dynamic programming algorithm for Weighted Task Selection
