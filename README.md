
**Table of Content**
- [Algorithms](#algorithms)
  - [General Approaches](#general-approaches)
    - [Brute force](#brute-force)
    - [Greedy](#greedy)
    - [Dynamic Programming](#dynamic-programming)
    - [divide and Conquer](#divide-and-conquer)
    - [Backtracking](#backtracking)
    - [Frequency Counter](#frequency-counter)
    - [Multiple Pointers](#multiple-pointers)
    - [Sliding Window](#sliding-window)
    - [Recursion](#recursion)
  - [Sort](#sort)
    - [Selection sort](#selection-sort)
    - [Bubble sort](#bubble-sort)
    - [Insertion sort](#insertion-sort)
    - [Merge sort](#merge-sort)
    - [Quick sort](#quick-sort)
  - [Search](#search)
    - [Linear Search](#linear-search)
    - [Binary Search](#binary-search)
- [Data Structure](#data-structure)
    - [Array](#array)
    - [Linked List](#linked-list)
      - [Singly Linked List](#singly-linked-list)
      - [Double Linked List](#double-linked-list)
    - [Set](#set)
    - [Queue](#queue)
    - [Stack](#stack)
    - [HashList](#hashlist)
      - [Without Bucket](#without-bucket)
      - [With Bucket](#with-bucket)
    - [Tree](#tree)
      - [Heap](#heap)
- [Challenges](#challenges)


# Algorithms

## General Approaches

### Brute force
- Brute Force Algorithms are exactly what they sound like straightforward methods of solving a problem that rely on sheer computing power and trying every possibility rather than advanced techniques to improve efficiency.
- A brute force approach is an approach that `finds all the possible solutions` to find a satisfactory solution to a given problem. The brute force algorithm `tries out all the possibilities` till a satisfactory solution is not found.

<!-- TODO: Code Examples -->

[Find substring](https://www.youtube.com/watch?v=M9azY7YyMqI&list=PL3edoBgC7ScV9WPytQ2dtso21YrTuUSBd)

### Greedy
A greedy algorithm is an approach for solving a problem by `selecting the best option available at the moment`. It doesn't worry whether the current best result will bring the overall optimal result.

The algorithm never reverses the earlier decision even if the choice is wrong. It works in a top-down approach.

<!-- TODO: Code Examples -->

### Dynamic Programming
- Dynamic programming is a technique that `breaks the problems into sub-problems`, and `saves the result` for future purposes so that we do not need to compute the result again. The subproblems are optimized to optimize the overall solution is known as optimal substructure property. `The main use of dynamic programming is to solve optimization problems`. Here, optimization problems mean that when we are trying to find out the minimum or the maximum solution of a problem. The dynamic programming guarantees to find the optimal solution of a problem if the solution exists.

- Dynamic Programming is mainly `an optimization over plain recursion`. Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming. `The idea is to simply store the results of subproblem`, so that we do not have to re-compute them when needed later. This simple optimization `reduces time complexities from exponential to polynomial`.

<!-- TODO: Code Examples -->


### divide and Conquer
Divide and Conquer is an algorithmic pattern. In algorithmic methods, the design is to take a dispute on a huge input, break the input into minor pieces, decide the problem on each of the small pieces, and then merge the piecewise solutions into a global solution. This mechanism of solving the problem is called the Divide & Conquer Strategy.

Divide and Conquer algorithm consists of a dispute using the following three steps.


1. **Divide** the original problem into a set of subproblems.
2. ***Conquer:*** Solve every subproblem individually, recursively.
3. ***Combine:*** Put together the solutions of the subproblems to get the solution to the whole problem.


![Divide](https://static.javatpoint.com/tutorial/daa/images/divide-and-conquer-introduction.png)

Examples:
- Binary Search
- Sorting (merge sort, quick sort)
- Maximum and Minimum Problem
- Tower of Hanoi.
<!-- TODO: Code Examples -->


### Backtracking
Backtracking is one of the techniques that can be used to solve the problem. We can write the algorithm using this strategy. 

It uses the `Brute force search` to solve the problem, and the brute force search says that for the given problem, we `try to make all the possible solutions` and `pick out the best solution from all the desired solutions`. 

This rule is also followed in dynamic programming, but dynamic programming is used for solving optimization problems. In contrast, backtracking is not used in solving optimization problems. Backtracking is used when `we have multiple solutions`, and we `require all those solutions`.

Backtracking can be defined as a general algorithmic technique that `considers searching every possible combination` in order to solve a computational problem.

Example:
[Generate Parentheses](https://youtu.be/Peq4GCPNC5c?t=1602)

<!-- TODO: Code Examples -->

### Frequency Counter
[link to an article](https://medium.com/nerd-for-tech/problem-solving-patterns-frequency-counter-20205a1ecfb7)

One of the most helpful problem solving patterns in computer science is known as the frequency counter pattern. Commonly used on `arrays` and `strings`, it is named frequency counter because when we use it, `we create an object or set to store the elements in our string or array, along with how many times they occur in that string or array`. More specifically, the element is usually a key in the object, and the value for that key is how many times that element is found.

Often, using a frequency counter will `help to avoid using a nested loop`, thus reducing the time complexity of our algorithm. Frequency counters can easily take an operation that would be `O(N²) down to a much more palatable O(N)`. The reason that it can be applied to problems that arrays and strings specifically is because strings are considered array-like objects in JavaScript, therefore you can both access and perform operations on an index of a string with the exact same syntax you could use on an array.

**Example:** Check two arrays have all of each others value? O(n)
```javascript
function sameSquared(firstArr, secondArr) {
  if (!firstArr || !secondArr) return false;
  if (firstArr.length !== secondArr.length) return false;

  const lookup = {};
  for (value of firstArr) {
    lookup[value * value] = (lookup[value * value] || 0) + 1;
  }
  for (secondValue of secondArr) {
    if (!lookup[secondValue]) return false;
    lookup[secondValue] -= 1;
  }
  return true;
}
```

O(n)
```javascript
function validAnagram(str1: string, str2: string): boolean {
    if (str1.length !== str2.length) {
        return false;
    }

    const frequencyCount1 = {};
    const frequencyCount2 = {};

    for (let value of str1) {
        frequencyCount1[value] = (frequencyCount1[value] || 0) + 1;
    }
    for (let value of str2) {
        frequencyCount2[value] = (frequencyCount2[value] || 0) + 1;
    }

    for (let key in frequencyCount1) {
        if (frequencyCount1[key] !== frequencyCount2[key]) {
            return false;
        }
    }

    return true;
}

```
### Multiple Pointers

[link to an article](https://medium.com/@kasiarosenb/algorithms-multiple-pointers-9843e1b5f1e1)

[link to an article](https://medium.com/@seanoughton/problem-solving-patterns-multiple-pointers-2dae827d154d)

Create `pointers or values` that correspond to an `index or position` and move `towards the beginning`, `end` or `middle` based on a `certain condition`. You can use it on some sort of linear structure, like an array, string or a linked list, to search for a pair of values, or searching for something that meets a condition. You use two reference points in the linear structure, and you work toward the middle.

**Example:** Write a function called sumZero which accepts a sorted array of integers. The function should find the first pair, where the sum is 0. Return an array that includes both values that sum to zero or undefined if a pair does not exist. This will only work with a sorted array. You move one pointer at a time, one side at a time. You move one pointer and test, then if the test is returns false, you move the other pointer and test.

O(n)
```javascript
// https://medium.com/@kasiarosenb/algorithms-multiple-pointers-9843e1b5f1e1
function sumZero(arr)
{
let left = 0;
let right = arr.length - 1;

while(left<right)
{
  let sum = arr[left] - arr[right];

  if (sum === 0)
  {
    return [arr[left],arr[right]];
  }
  else if (sum > 0)
  {
    right --;
  }
  else
  {
    left ++;
  }
}
}

sumZero ([-4,-3,-2,-1,0,1,2,5])
```


```javascript
// https://medium.com/@kasiarosenb/algorithms-multiple-pointers-9843e1b5f1e1
function countUniqueValues(arr){
    if(arr.length === 0) return 0;
    let i = 0;
    for(var j=1; j<arr.length; j++) {
        if(arr[j] !== arr[i]) {
          i++;
          arr[i] = arr[j]
        }
    }    
    return i+1;  
}

// https://github.com/tajpouria/algorithms-and-data-structures-cheat-sheet
function countUniqueValues(arr: number[]): number {
    let pointer = 0;
    let count = 0;
    while (pointer < arr.length) {
        if (arr[pointer] === arr[pointer + 1]) {
            pointer++;
        } else {
            count++;
            pointer++;
        }
    }

    return count;
}

```

### Sliding Window
[link to an article](https://sarahdepalo.hashnode.dev/algorithm-patterns-sliding-window)

The sliding window technique essentially involves creating a window which can either be an array or number that “slides” from one position to another. Depending on a certain condition, the window will either increase or close (creating a new window). This technique is `useful for keeping track of a subset of contiguous data in an array or string`. Common examples of when you might use this technique include finding the `longest sequence of unique characters`, calculating the `max sum of consecutive elements` in an array, and much more.

**Example:** Calculate the max sum of n consecutive elements in an array?

```javascript
// https://sarahdepalo.hashnode.dev/algorithm-patterns-sliding-window
const maxSubArraySum = (arr, n) => {
  let maxSum = 0;
  let tempSum = 0;
  if (arr.length < n) return null;
  for (let i = 0; i < n; i++) {
    maxSum += arr[i];
  }
  tempSum = maxSum;
  for (let i = n; i < arr.length; i++) {
    tempSum = tempSum - arr[i - n] + arr[i];
    maxSum = Math.max(maxSum, tempSum);
  }
  console.log(maxSum)
}

maxSubArraySum([2, 6, 9, 2, 1, 8, 2, 6], 2) // 15
```

**Example:** Given an array and a positive number k, check whether the array contains any duplicate elements within the range k. If k is more than the array’s size, the solution should check for duplicates in the complete array. Return true and the repeated number or return false if there are no duplicates.

```javascript
const findDuplicatesWithinRange = (arr, k) => {
  let window = [];

  for (let i = 0; i < arr.length; i++) {
    if (window.includes(arr[i])) {
      return `true, the first repeated number is ${arr[i]}`
    }
    window.push(arr[i])
    if (i >= k) {
      window.shift()
    }

  }
  return false
}

console.log(findDuplicatesWithinRange([1, 2, 3, 4, 5, 6, 7, 5], 4)) // "True, the repeated number was 5"
```
### Recursion

## Sort
In this section, there are some of sorting algorithms with their `complexity` and `explanation`.

Also there are some other sorting mention below that worse to know.
> Heap sort,
> Counting sort,
> Radix sort,
> Bucket sort,

### Selection sort
### Bubble sort
### Insertion sort
### Merge sort
### Quick sort


## Search

### Linear Search
### Binary Search


# Data Structure
### Array
### Linked List
#### Singly Linked List
#### Double Linked List
### Set
### Queue
### Stack
### HashList
#### Without Bucket
#### With Bucket
### Tree
#### Heap

# Challenges