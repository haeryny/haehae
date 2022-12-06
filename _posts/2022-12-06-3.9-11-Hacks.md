---
toc: true
layout: post
comments: true
description: All Videos
categories: [markdown]
title: Unit 3 Sections 9 and 11
---

## 3.9 Video 1
### Essential Knowledge
- Algorithms can be written in different ways and still accomplish the same tasks
- Algorithms that appear similar can yield different side effects or results
- Some conditional statements can be written as equivalent Boolean expressions
- Some Boolean expressions can be written as equivalent conditional statements
- Different algorithms can be developed or used to solve the same problem

### Dice Game
Do these two algorithms give the same results?

```python
print("What did you roll on the dice?")
diceRoll = int(input())
if diceRoll >= 4:
    print("Nice roll!")
else:
    if diceRoll >= 2:
        print("Meh... You can do better")
    else:
        print("That was not a great roll!")
```

```python
print("What did you roll on the dice?")
diceRoll = int(input())
if diceRoll >= 4:
    print("Nice roll!")
if diceRoll >= 2:
    print("Meh... You can do better")
if diceRoll < 2:
    print("That was not a great roll!")
```

- In what instances do the algorithms yield different results for the same input?
- Why does this happen?

### Can we adjust the second algorithm to yield the same results?

```python
print("What did you roll on the dice?")
diceRoll = int(input())
if diceRoll >= 4:
    print("Nice roll!")
if diceRoll >= 2 and diceRoll < 4:
    print("Meh... You can do better")
if diceRoll < 2:
    print("That was not a great roll!")
```

**What can be taken away from this?**
- Small changes/mistakes can have a big impact on the result
- There is often more than one way to achieve the same result

### Conditional vs Boolean
- How could this conditional scenario be replaced with a boolean scenario?   

- IF (isHoliday)   
- {   
    - school⟵false   
- }   
- ELSE   
- {   
    - IF(isWeekday)   
    - {   
        - school⟵true   
    - }   
    - ELSE   
    - {   
        - school⟵false   
    - }   
- }   

**What needs to be true and what needs to be false in order for you to go to school?**
- First conditional: If isHoliday is true, you do not need to go to school
- Second conditional: If isWeekday is true, you do need to go to school. However, if it is false, school also becomes false

**Therefore, in pseudo code, this statement could be written as:**
- school⟵((NOT (isHoliday)) AND (isWeekday))
- Keep in mind that both of these statements yield the same results, and neither of them are incorrect

### More Comparing Algorithms
The algorithms below are to sum the odd numbers from 1 to 9 (1+3+5+7+9). Do they each work as intended?

1. 
- sum⟵1
- counter⟵3
- REPEAT 4 TIMES
    - sum⟵sum + counter
    - counter⟵counter + 2
- DISPLAY sum

2. 
- sum⟵0
- counter⟵9
- REPEAT UNTIL counter < 1
    - sum⟵sum + counter
    - counter⟵counter - 2
- DISPLAY sum

**Why is it important to understand that algorithms can be written in different ways and still accomplish the same tasks?**

## 3.9 Video 2
### Essential Knowledge 
- Algorithms can be created from an idea, 
  by combining existing algorithms, 
  or by modifying existing algorithms.

### Vocab
- Iteration: Repeating steps, or instructions over and over again. 
( this could be also often called a loop ) 
- Selection: is a decision or question. At some point in an algorithm there may need to be a question because the algorithm has reached a step where one or more options are available.

### Create an Algorithm

<a href="https://trentcardall.github.io/period4yeung/images/robotanswer.png">
    <img src="https://trentcardall.github.io/period4yeung/images/example1triangle.png">
</a>

- Create an algorithm to move the robot to the gray square for the grid of squares on the right.
- The robot is represented by a triangle, which is initially facing towards the top of the grid.
- The robot can move into a white or gray square but cannot move into a black region.

**Answer is hidden so you guys don't cheat**

- You might notice that certain parts would be repeated if you listed all the steps.
- To more easily represent the algorithm, without showing every step, we could use iteration.
- By using iteration, we can better see the flow of the algorithm.
- The algorithm below uses the procedure goalReached, which returns true if the robot is in gray square and returns false otherwise.
![photo]({{site.baseurl}}/images/flowchart robot.png)
- We can represent this algorithm using pseudocode    

    
- REPEAT UNTIL (goalReached)
- {
    - MOVE_FORWARD ()
    - ROTATE_RIGHT ()
    - MOVE_FORWARD ()
    - ROTATE_LEFT ()
- }

### Practice Question

Choose which algorithm that uses selection and/or iteration to determine the cost of one item in the store is correct

The display at the store says the following:

All Green Tag Items - 25% off
All Red Tag Items - 60% off

Suppose that the tax on all items is 10%

**Algorithm A:**

- DISPLAY ("What is the cost of the item?")
- cost←INPUT ()
- IF (greenTag)
- {
    - cost ← 0.75 * Cost 
- }
- IF (redTag)
- {
    - cost ← 0.40 * Cost 
- }
- cost ← 1.10 * cost

**Algorithm B:**

- DISPLAY (What is the cost of the item)
- cost←INPUT ()
- IF (greenTag)
- {
    - cost ← 0.75 * Cost 
- }
- IF (redTag)
- {
    - cost ← 1.10 * cost
- }
- cost ← 0.40 * Cost


## 3.9 Video 3

### Essential Knowledge 
- Knowledge of existing algorithms can help in constructing new ones. Some existing algorithms include:
Determining the maximum or minimum value of two or more numbers.
Computing the sum or average of two or more numbers.
Identifying if an integer is or is not evenly divisible by another integer.
Determining a robot's path through a maze.
- Using existing correct algorithms as building blocks for constructing another algorithm has benefits such as reducing development time, reduce testing, and simplifying the identification of errors.

### Vocab 
- Algorithm: A process or set of rules to be followed in calculations or other problem solving operations, especially by a computer.

### Another Robot Example
How can we make this work?
- Create a algorithm to move the robot to the grey square for the grid above
- The robot is represented by a triangle
- The robot can move into white and grey squares but cannot move into a black square
![]({{site.baseurl}}/images/incorrectexample.png)
![]({{site.baseurl}}/images/algorithmforvideo3.png)

- What is wrong with the algorithm above?
- How do we fix this?
- [By allowing it to move left](https://trentcardall.github.io/period4yeung/images/2ndgridanswer.png)

## 3.11
### Learning Objective
- For binary search algorithims
    - Determine the number of iterations required to find a value in a data set. 
    - Explain the requirements necessary to complete a binary search.
- The binary search algorithm starts at the middle of a sorted data set of numbers and eliminates half of the data; this process repeats until the desired value is found or all elements have been eliminated.
- Data must be in sorted order to use the binary search algorithm 
- A binary search is often more efficient than sequential/linear search when applied to sorted data.

### Essential knowledge
- Imagine you had to search for a number in a huge set. How would you do it? Would you pick randomly or would you put them in order first?

### Sequential Search 
- For the sake of this search lets line up the numbers
- It doesn't have to be in order 
- In this method you go down the line to find the number you are looking for
- For a Sequential Search you compare each number to the number you are searching for
- If it is not the number you are looking for you move on. (inefficient method)
- You can also use this method for strings as well. 
image(13)

### Binary Search
- While using Binary Search you have to put the group of numbers from ascending or descending order
- What the computer does it takes the lowest index and the highest index, adds them and then divides that value by 2. 
- This gets the middle value and starts the search at the middle of the group. 
![]({{site.baseurl}}/images/image (13).png)
- Go to the respective index and pull the element, if this is not the desired number then go to the left and the right to and repeat the same process for the left and the right without including the index of the middle number. (efficient method)
![]({{site.baseurl}}/images/image (14).png)
- To put the efficiency of the binary search method into context if you have a list of 600 numbers the maximum amount of attempts it will take to get the number is 10. (1 level of tree is one search, the algorithm goes to the side of which the number is on the tree)
![]({{site.baseurl}}/images/image (15).png)
- This method also applies to strings as well because only the indexes are getting compared. As long as the user can put it in an order (preferably alphabetical order) to tell the algorithm which side of the middle index to go to next then it is possible to use 


### Practice Problems
1. Which is a plausable way to pattern your numbers for binary search. 

    a. [1,4,5,2,3]
    b. [24,22,23,28,30]
    c. [5,6,7,8,2]
    d. [1,2,3,4,5]

2. How many checks would it take to print out 20 using sequential search 

    - [1, 3, 4, 5, 7, 8, 10 ,20]

3. How many checks would it take to print out 30 using binary search 

    - [1, 2, 3, 4, 6, 8, 9, 11, 30]

4. Using Binary Search how many checks would it take to find the word kiwi. 

    - [Apple, Banana, Kiwi, Mango, Strawberry]

## Rap
- Each group has 2 minutes to write a 3 line rap about what they learned. One volunteer will rap their group's lines and will receive a reward

## Hacks
1. **Write this Boolean statement in the form of a conditional (if/else) statement:**
stayInside⟵((isCold) OR (isRaining))

2. **Create an algorithm that uses selection and/or iteration that will represent one player's complete turn.**

    - During a turn, each player gets 4 attempts/chances to get the greatest number possible.

    - During each attempt, the player will use a random number generator to select a random number from 1 to 10.

    - After they have had 4 chances, their score is the greatest number they received from the random number generator, and their turn is over.

3. **Create an algorithm that will allow the arrow to reach the gray square:**
![]({{site.baseurl}}/images/examplevideo3.png)

4. Make a binary search tree of different the list [1,2,3,4,6,9,11,69]

5. Explain thorughly how to find the number 69 in the list above (use key words)

6. Make a diagram explaining how you found the list (not tree, include equation)

7. Put this list of strings in a order that can be used for binary search ["store","Market","Walmart",Target","Ralphs"]

8. Explain why Binary Search is more efficient than Sequential Search

9. [64,36,16,11,9] Explain which number you are finding, how many check it would take, and make a binary search tree

5. **Extra question if elected official gets answer wrong:**
    - Create two different algorithms which yield the same results
