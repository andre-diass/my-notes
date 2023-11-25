# Algorithms

<!-- TOC -->
- [Big O](#big-o)
  - [Introduction](#introduction)
  - [Time and Space Complexity](#time-and-space-complexity)
  - [Fuzzy Count](#fuzzy-count)
  - [Examples of `f(n)`](#examples-of-f-n)
  - [Rules of Thumb](#rules-of-thumb)
  - [When to Use Objects](#when-to-use-objects)
    - [Object Methods](#object-methods)
  - [When to Use Arrays](#when-to-use-arrays)
    - [Big O of Arrays](#big-o-of-arrays)
    - [Big O of Arrays Operations](#big-o-of-arrays-operations)
- [Problem Solving](#problem-solving)
  - [Understand the Problem](#understand-the-problem)
  - [Explore Examples](#explore-examples)
  - [Break It Down](#break-it-down)
  - [Simplify](#simplify)
  - [Refactoring Questions](#refactoring-questions)
- [Recursion](#recursion)
  - [Base Case](#base-case)
- [Search Algorithms: Binary Search, Linear Search, and String Search](#search-algorithms-binary-search-linear-search-and-string-search)
  - [Binary Search](#binary-search)
    - [Binary Search Pseudo Code](#binary-search-pseudo-code)
- [Sorting Algorithms: Bubble Sort, Selection Sort](#sorting-algorithms-bubble-sort-selection-sort)
  - [Bubble Sort Pseudo Code](#bubble-sort-pseudo-code)
  - [Selection Sort](#selection-sort)
    - [Selection Sort Pseudo Code](#selection-sort-pseudo-code)


## Big O
- Big O notation is a way to formalize fuzzy counting
  
- It allows us to talk in a very formal way about how the runtime of an algorithm grows as the inputs 
grow.

- It's a way of describing the relationship between the input to a function or as it grows, and how that 
changes the runtime of that function, the relationship between the input size and then the time relative 
to that input.

- Big O can help define time complexity and space complexety of an algorithm. This is useful discuss trade offs in different implementations, identifying crashes or parts of the code that are inneficient

- Regardless of the times of operations in an algorithm we are always going to look at the fuzzy count. how proportionally operations increases with `n` 
- `f(n)` can be: 

  * (f(n) = n) linear 

  * (f(n) = n^2  ) quadratic 

  * (f(n) = 1) constant
 
### RULES OF THUMB 
(1) Constants and smaller terms dont matter <br>
(2) Arithmetic operations are constant <br>
(3) Variable assignment is constant <br>
(4) Accessing elements in an array (by index) or object (by key) is constant <br>
(5) In a loop, the the complexity is the length of the loop times the complexity of whatever happens inside of the loop <br>
(6) Most primitives (booleans, numbers, undefined, null) are constant space <br>
(7) Strings require O(n) space (where n is the string length) <br>
(8) Reference types are generally O( n), where n is the length (for arrays) or the number of keys (for objects) <br>


### WHEN TO USE OBJECTS
When you don't need order <br>
When you need fast access / insertion O(1), removal O(1), searching O(N) and access O(1) <br>

- Big O of Object Methods: <br>
`Object.keys` -   O(N) <br>
`Object.values` -   O(N) <br>
`Object.entries` -   O(N) <br>
`hasOwnProperty` -   O(1) <br>

### WHEN TO USE ARRAYS
When you need order <br>
When you need fast access / insertion and removal (sort of....) <br>

- Big O of Arrays <br>
`Insertion` -   It depends on where... If I insert at the beginning all indexes change. So it's O(N). Insertion at the end is fine <br>
`Removal` -   It depends on where... the same for removal as insertion. beggining and end have differences. end always better <br> 
`Searching` -   O(N) <br>
`Access` -   O(1) <br>

- Big O of Arrays Operations
`push` -   O(1) <br>
`pop` -   O(1) <br>
`shift` -   O(N) <br>
`unshift` -   O(N) <br>
`concat` -   O(N) <br>
`slice` -   O(N) <br>
`splice` -   O(N) <br>
`sort` -   O(N * log N) <br>
`forEach/map/filter/reduce/etc.` -   O(N) <br>

## Problem Solving
### (1) Understand the Problem 
- Can I restate the problem in my own words? 
- What are the inputs that go into the problem? 
- What are the outputs that should come from the solution to the problem? 
- Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problem? (You may not be able to answer this question until you set about solving the problem. That's okay; it's still worth considering the question at this early stage.)
- How should I label the important pieces of data that are a part of the problem?

### (2) Explore Examples 
- Start with Simple Examples 
- Progress to More Complex Examples 
- Explore Examples with Empty Inputs 
- Explore Examples with Invalid Inputs

### (3) Break It Down 
- Explicitly write out the steps you need to take. 
- This forces you to think about the code you'll write before you write it, and helps you catch any lingering conceptual issues or misunderstandings before you dive in and have to worry about details (e.g. language syntax) as well.

### (4) Simplify; If I can't answer right away
- Find the core difficulty in what you're trying to do 
- Temporarily ignore that difficulty 
- Write a simplified solution 
- Then incorporate that difficulty back in

### (5) Refactoring Questions
- Can you check the result? 
- Can you derive the result differently? 
- Can you understand it at a glance? 
- Can you use the result or method for some other problem? 
- Can you improve the performance of your solution? 
- Can you think of other ways to refactor? 
- How have other people solved this problem?

## Recursion
Recursion is a process (a function in this case) that calls itself. Invoke the same function with a different input until you reach your base case.

### Base Case 
The condition when the recursion ends.

## Search Algorithms: Binary Search, Linear Search, and String Search 
### Binary Search
Binary search is a much faster form of search. Rather than eliminating one element at a time, you can eliminate half of the remaining elements at a time. Binary search only works on sorted arrays! Binary search is O(log n), because every time the array increases by its size squared, the number of steps taken increases by one.

#### Binary Search Pseudo Code
- This function accepts a sorted array and a value 
- Create a left pointer at the start of the array, and a right pointer at the end of the array 
- While the left pointer comes before the right pointer: 
  - Create a pointer in the middle 
  - If you find the value you want, return the index 
  - If the value is too small, move the left pointer up 
  - If the value is too large, move the right pointer down 
  - If you never find the value, return -1

## Sorting Algorithms: Bubble Sort, Selection Sort 
### Bubble Sort Pseudo Code 
Start looping from with a variable called i the end of the array towards the beginning <br>
Start an inner loop with a variable called j from the beginning until i - 1 <br>
If arr[j] is greater than arr[j+1], swap those two values! <br>
Return the sorted array <br>
Similar to bubble sort, but instead of first placing large values into sorted position, it places small values into sorted position. Store the first element as the smallest value you've seen so far. Compare this item to the next item in the array until you find a smaller number. If a smaller number is found, designate that smaller number to be the new "minimum" and continue until the end of the array. If the "minimum" is not the value (index) you initially began with, swap the two values. Repeat this with the next element until the array is sorted.

### Selection Sort
Similar to bubble sort, but instead of first placing large values into sorted position, it places small values into sorted position <br>
Store the first element as the smallest value you've seen so far. <br>
Compare this item to the next item in the array until you find a smaller number. <br>
If a smaller number is found, designate that smaller number to be the new "minimum" and continue until the end of the array. <br>
If the "minimum" is not the value (index) you initially began with, swap the two values. <br>
Repeat this with the next element until the array is sorted. <br>
