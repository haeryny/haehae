---
toc: true
layout: post
categories: [markdown, week27]
title: Space Time Complexity Hacks
---

## Practice
### Question 1
Input:
```{python}
int a = 0, b = 0;
for (i = 0; i < N; i++) {
    a = a + rand();
}
for (j = 0; j < M; j++) {
    b = b + rand();
}
```
Output:

O(N + M) time, O(1) space

### Question 2
Input:
```{python}
int a = 0;
for (i = 0; i < N; i++) {
    for (j = N; j > i; j--) {
        a = a + i + j;
    }
}
```
Output:

O(N*N)

### Question 3
Input:
```{python}
int i, j, k = 0;
for (i = n / 2; i <= n; i++) {
    for (j = 2; j <= n; j = j * 2) {
        k = k + n / 2;
    }
}
```
Output: 

O(nLogn)

### Question 4
What does it mean when we say that an algorithm X is asymptotically more efficient than Y? 

> Answer: X will always be a better choice for large inputs

### Question 5
Input:
```{python}
int a = 0, i = N;
while (i > 0) {
    a += i;
    i /= 2;
}
```
Output:

O(log N)

### Question 6
Which of the following best describes the useful criterion for comparing the efficiency of algorithms?

> Answer: Both time and memory because by comparing the efficiency of an algorithm depends on the time and memory taken by  an algorithm. The algorithm which runs in lesser time and takes less memory even for a large input size is considered a more efficient algorithm.

### Question 7
How is time complexity measured?

> Answer: By counting the number of primitive operations performed by the algorithm on a given input size.

### Question 8
Input:
```{python}
for(var i=0;i<n;i++)
    i*=k
```

Output:
O(logkn)

### Question 9
Input:
```{python}
int value = 0;
for(int i=0;i<n;i++)
    for(int j=0;j<i;j++)
      value += 1;
```

Output:
n(n-1)

## Research
Do some basic research on the different types of sorting algorithms and their time complexity.

### What is Time Complexity?
Time Complexity is defined as the number of times a particular instruction set is executed rather than the total time taken. It is because the total time took also depends on some external factors like the compiler used, processor’s speed, etc.

Types Of Time Complexity:

1. Best Time Complexity: Define the input for which algorithm takes less time or minimum time. In the best case calculate the lower bound of an algorithm. Example: In the linear search when search data is present at the first location of large data then the best case occurs.
2. Average Time Complexity: In the average case take all random inputs and calculate the computation time for all inputs. And then we divide it by the total number of inputs.
3. Worst Time Complexity: Define the input for which algorithm takes a long time or maximum time. In the worst calculate the upper bound of an algorithm. Example: In the linear search when search data is present at the last location of large data then the worst case occurs.

