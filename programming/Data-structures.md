# Data structures and algorithms concepts

### Technical questions

- how to prepare:
  - solve the problem without looking at the solution
  - write code on paper
  - test code on paper
  - try solution on a computer, keep track of mistakes
- **must-have topics**:
  - DS: linked lists, trees & graphs, stacks & queues, heaps, vectors, hash tables
  - algorithms: breadth-first, depth-first search, binary search, merge sort, quick sort
  - concepts: bit manipulation, memory, recursion, dynamic programming, big O

### Big O

- describes efficiency of algorithms

- **time complexity**:
  - for transfering a large file, electronic transfer would be O(s) - scales with the size of the file, whereas airplane transfer would be O(1) - constant time
  - other common examples are $O(log N)$, $O(N log N)$, $O(N)$, $O(N^2)$ and $O(2^N)$
  - O - upper bound on time (could be N or $N^2$ etc)
  - $\Omega$ - lower bound (can’t be faster than)
  - $\Theta$ - both O and $\Omega$
  - in the industry, Big O usually means the tightest description
  - cases (example - quicksort)
    - best case - elements are equal, sort traverses once
    - worst case - traverses N^2 times
    - expected case - somewhere in between, N log N
- **space complexity**:
  - parallel to time complexity
  - stack space in recursive functions also counts
- constants (e.g. 2N) are usually dropped, so are the non-dominant terms (e.g. $N^2+N$)
- **add vs multiply:**
  - add - separate loops
  - multiply - nested loops
- amortized time:
  - if we have a dynamic array, it’s implemented with a list that is increased 2x each time it’s full, so most of the time it’s O(1), but sometimes O(N)
- log(N) runtimes:
  - if the number of elements is halved each time (e.g. binary search), the time is logarithmic
  - base of the log does not matter - logs of different bases are different by a constant factor (but exponents are not)
- recursive runtimes - $O(branches^{depth})$
- common mistake - if loops have the same input, then the runtime is O(N), but if they have arrays A and B as input, then O(len(A)*len(B))
- **examples**
  - 1:
    - take array of strings, sort each string, then sort the full array
    - you cannot use N here, because there are different lengths (string and array)
    - s - length of string
    - a - length of array
    - sorting a strings - a*(s log s)
    - sorting array - a*s log a (\*s because of strings comparison)
    - add all together - a*s(log a + log s)
  - 2:
    - isPrime (checks only up to sqrt(n))
    - worst case - stops at sqrt(n)
  - 3:
    - recursive n! resolves in O(n) time
  - **ADD: string permutations, Fib variations, memoization, powers**
  - **SOLVE: additional problems**

### Data structures

#### Linked lists

#### Trees

#### Stacks

#### Vectors

### Algorithms

#### Searches

#### Sorts

### Other concepts

