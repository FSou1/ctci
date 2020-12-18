# CTCI

## Big O

1. What is its runtime?

```
int product(int a, int b) {
  int sum = 0;
  for (int i = 0; i < b; i++) {
    sum += a;
  }
  return sum;
}
```

<details>
  <summary>Answer</summary>
  O(b)
</details>

2. What is its runtime?

```
int power(int a, int b) {
  if (b < 0) {
    return 0;
  } else if (b == 0) {
    return 1;
  } else {
    return a * power(a, b - 1);
  }
}
```

<details>
  <summary>Answer</summary>
  O(b)
</details>

3. What is its runtime?

```
int mod(int a, int b) {
  if (b <= 0) {
    return -1;
  }
  int div = a / b;
  return a - div * b;
}
```

<details>
  <summary>Answer</summary>
  O(1)
</details>

4. What is its runtime?

```
int div(int a, int b) {
  int count = 0;
  int sum = b;
  while (sum <= a) {
    sum += b;
    count++;
  }
  return count;
}
```

<details>
  <summary>Answer</summary>
  O(a / b)
</details>

5. What is its runtime?

```
int sqrt(int n) {
  for (int guess = 1; guess * guess <= n; guess++) {
    if (guess * guess == n) {
      return guess;
    }
  }
  return -1;
}
```

<details>
  <summary>Answer</summary>
  O(sqrt(n))
</details>

6. If a binary search tree is not balanced, how long might it take (worst case) to find an element in it?

<details>
  <summary>Answer</summary>
  O(n)
</details>

7. You are looking for a specific value in a binary tree, but the tree is not a binary search tree. What is the time complexity of this?

<details>
  <summary>Answer</summary>
  O(n)
</details>

8. What is its runtime?

```
int sumDigits(int n) {
  int sum = 0;
  while (n > 0) {
    sum += n % 10;
    n /= 10;
  }
  return sum;
}
```

<details>
  <summary>Answer</summary>
  O(|n|) or <a href="https://stackoverflow.com/a/50262470/2524304">O(logn)</a>
</details>

9. What is its runtime?

```
int intersection(int[] a, int[] b) {
  mergesort(b);
  int intersect = 0;
  
  for(int x : a) {
    if(binarySearch(b, x) >= 0) {
      intersect++;
    }
  }
  
  return intersect;
}
```

<details>
  <summary>Answer</summary>
  O(blogb) + O(alogb)
</details>

## Technical questions

For each of this topics, make sure you understand how to use and implement them and, where applicable, the space and time complexity.

Data structures:
* Linked lists
* Trees, Tries, & Graphs
* [Stacks](https://github.com/FSou1/typescript-algorithms/tree/master/src/data-structures/stack) & [Queues](https://github.com/FSou1/typescript-algorithms/blob/master/src/data-structures/queue)
* Heaps
* Vectors / ArrayLists
* Hash Tables

Algorithms:
* [Breadth-First Search](https://github.com/FSou1/typescript-algorithms/blob/master/src/algorithms/graph/breadth-first-search)
* [Depth-First Search](https://github.com/FSou1/typescript-algorithms/blob/master/src/algorithms/graph/depth-first-search)
* Binary Search
* [Merge Sort](https://github.com/FSou1/typescript-algorithms/blob/master/src/algorithms/sort/merge)
* Quick Sort

Concepts:
* Bit Manipulation
* Memory (Stack vs Heap)
* Recursion
* Dynamic Programming
* Big O Time & Space
