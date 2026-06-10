# Introduction
Sparse Table is a data structure, that allows answering range queries. It is a concept used for fast queries on a set of static data (elements do not change). It does preprocessing so that the queries can be answered efficiently. 

## Advantage
It can answer most range queries in 
$O(\log n)$ , but its true power is answering range minimum queries (or equivalent range maximum queries). For those queries it can compute the answer in 
$O(1)$  time.

## Disadvantage
The only drawback of this data structure is, that it can only be used on immutable arrays. This means, that the array cannot be changed between two queries. If any element in the array changes, the complete data structure has to be recomputed.
