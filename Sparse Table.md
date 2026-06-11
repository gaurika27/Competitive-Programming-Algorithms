# Introduction
Sparse Table is a data structure, that allows answering range queries. It is a concept used for fast queries on a set of static data (elements do not change). It does preprocessing so that the queries can be answered efficiently. 

## Advantage
It can answer most range queries in 
$O(\log n)$ , but its true power is answering range minimum queries (or equivalent range maximum queries). For those queries it can compute the answer in 
$O(1)$  time.

## Disadvantage
The only drawback of this data structure is, that it can only be used on immutable arrays. This means, that the array cannot be changed between two queries. If any element in the array changes, the complete data structure has to be recomputed.

## Intuition
Any non-negative number can be uniquely represented as a sum of decreasing powers of two. This is just a variant of the binary representation of a number. E.g. 
$13 = (1101)_2 = 8 + 4 + 1$ . For a number  
$x$  there can be at most 
$\lceil \log_2 x \rceil$  summands.

By the same reasoning any interval can be uniquely represented as a union of intervals with lengths that are decreasing powers of two. E.g. 
$[2, 14] = [2, 9] \cup [10, 13] \cup [14, 14]$ , where the complete interval has length 13, and the individual intervals have the lengths 8, 4 and 1 respectively. And also here the union consists of at most 
$\lceil \log_2(\text{length of interval}) \rceil$  many intervals.

The idea is to precompute the minimum values for all subarrays whose lengths are powers of two and store them in a table so that any range-minimum query can be answered in constant time. We build a 2D array lookup where lookup[i][j] holds the minimum of the subarray starting at i with length 2^j (j varies from to Log n where n is the length of the input array). For example lookup[0][3] contains minimum of range [0, 7] (starting with 0 and of size 23)
