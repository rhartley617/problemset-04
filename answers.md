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
With $b$ bits, we can represent $2^b$ distinct characters.  
This equation relates bits to alphabet size $|\sum|$:  
$2^b = |\sum|$  
Huffman coding normally varies the bit size of each letter according to its relative freqency in the document, with higher frequency characters receiving smaller sized codes.  
Because the freqency of each letter of the alphabet $\sum$ is the same in the documents we're considering, Huffman coding will assign each letter in $\sum$ to a leaf in a balanced tree, which will result in each letter having the same bit size. This size will increase with the total number of distict letters in the alphabet being used $|\sum|$.  
With an integer ceiling to account for cases where $|\sum|$ is odd, the size of each character will be: $b = \lceil\log_2|\sum|\rceil$  
Because each letter has the same cost and freqency, we're only concerned with the total number of letters $n$ and the cost of each letter when determining the total cost per document:  

    $\boxed{\text{Document coding cost} = n \cdot \lceil\log_2|\sum|\rceil}$

    This equation would be consitant across documents provided all character freqencies within the document remained the same.






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
