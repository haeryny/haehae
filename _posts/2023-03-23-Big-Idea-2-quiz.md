---
toc: true
layout: post
categories: [markdown, week27]
title: Big Idea 2 Questions
---

![image](https://user-images.githubusercontent.com/111464920/227345731-c4914dfe-9f22-4612-a263-997ffc496025.png)

### Questions I got Wrong

**Question 2:** A store uses binary numbers to assign a unique binary sequence to each item in its inventory. What is the minimum number of bits required for each binary sequence if the store has between 75 and 100 items in its inventory?

Wrong Answer: B

Right Answer: C

Explanation: Using 6 bits will only allow for up to 64 sequences because 2^6=64. Using 7 bits will allow for up to 128 sequences because 2^7=128. Therefore, a minimum of 7 bits are needed.

**Question 4:** In which of the following situations would it be most appropriate to choose lossy compression over lossless compression?

Wrong Answer: A

Right Answer: C

Explanation: In situations where minimizing data size or transmission time is maximally important, lossy compression algorithms are typically chosen.

**Question 19:** Which of the following sequences of steps can be used to identify the desired restaurant?

Wrong Answer: C

Right Answer: D

Explanation: Because the relative order of the rows is not changed when the filters are applied, the order in which the actions are performed does not matter. The filtering can occur either before or after the spreadsheet is sorted by rating.

**Question 20:** Which of the following expressions will evaluate to true if the restaurant should be counted and evaluates to false otherwise?

Wrong Answer: A

Right Answer: B

Explanation: This expression evaluates to true only for restaurants with the correct price range (when prcRange equals "lo" or "med") and the correct customer rating (when avgRating ≥ 4.0).

**Question 21:** Which of the following sequences of steps can be used to identify the desired entry?

Wrong Answer: A and C

Right Answer: B and D

Explanation: Filtering by photographer will remove any entries with unknown photographers. Filtering by year will remove any entries with unknown years. Sorting by year will sort the remaining entries in column C from least to greatest, putting the photograph with the lowest year value in the first row of the spreadsheet. Sorting by year will sort the spreadsheet on column C from least to greatest. Filtering by year will remove any entries with unknown years. Filtering by photographer will remove any entries with unknown photographers. Since the order of the entries is not affected by the filters, the photograph with the lowest year value will be in the first row of the spreadsheet.