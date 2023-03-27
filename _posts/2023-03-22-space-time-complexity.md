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

### Types of Sorting Algorithms

Sorting algorithms are methods used to organize data in a specific order. There are many types of sorting algorithms, each with its own time complexity. Here are some of the most common sorting algorithms and their time complexity:

|Types of Sorting Algorithms| Definition| Time Complexity|
|---------------------------|-----------|----------------|
|Bubble Sort                | Bubble Sort is a simple sorting algorithm that compares adjacent elements and swaps them if they are in the wrong order| The time complexity of Bubble Sort is O(n^2)|
|Selection Sort             | Selection Sort sorts an array by repeatedly finding the minimum element from the unsorted part of the array and putting it at the beginning| The time complexity of Selection Sort is O(n^2)|
|Insertion Sort             | Insertion Sort builds the final sorted array one item at a time. It works by comparing each element in the array to the elements before it and inserting it into the correct position| The time complexity of Insertion Sort is O(n^2)|
|Quick Sort                 | Quick Sort is a divide-and-conquer algorithm that works by selecting a "pivot" element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively| The time complexity of Quick Sort is O(n log n)|
|Merge Sort                 | Merge Sort is also a divide-and-conquer algorithm that works by dividing the array into two halves, sorting each half, and then merging the two halves back together| The time complexity of Merge Sort is O(n log n)|
|Heap Sort                  | Heap Sort is a comparison-based sorting algorithm that works by turning the array into a binary heap, and then repeatedly extracting the largest element from the heap and placing it at the end of the array| The time complexity of Heap Sort is O(n log n)|

Overall, the choice of sorting algorithm depends on the specific requirements of the problem at hand, including the size of the data set, the range of the values, and the desired efficiency of the algorithm.

## Hacks Questions

1. Why is time and space complexity important when choosing an algorithm?
> Time and space complexity are important when choosing an algorithm because they determine how much time and memory an algorithm will require to solve a problem. An algorithm that is efficient in terms of time and space complexity will be faster and require less memory than an algorithm that is not efficient, making it a better choice for solving larger problems or problems that need to be solved quickly. If the algorithm doesn't work, this is bad from both the perspective of a programmer and of a consumer. A consumer does not want to work with a laggy, slow program that fails to account for large amounts of data and programmers will find it difficult to work around processing algorithms that are very time-consuming.
2. Should you always use a constant time algorithm / Should you never use an exponential time algorithm? Explain? 
> No, you should not always use a constant time algorithm or never use an exponential time algorithm. The choice of algorithm depends on the specific problem being solved and the trade-offs between time and space complexity. In some cases, a constant time algorithm may not be able to solve the problem efficiently, while in other cases, an exponential time algorithm may be the only practical solution. It is important to consider the constraints and requirements of the problem at hand when choosing an algorithm.
3. What are some general patterns that you noticed to determine each algorithm's time and space complexity?
> Some general patterns to determine time and space complexity are analyzing loops, recursive functions, and nested data structures. For time complexity, counting the number of operations executed by an algorithm related to/caused by the input size is often used to determine time complexity. For space complexity, analyzing the amount of memory required to store data as a function of the input size is often used to determine space complexity.
