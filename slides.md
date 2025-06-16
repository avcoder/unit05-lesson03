---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Algorithms and Data Structures
Algorithms and Structural Foundations - part 3/8

- [ ] Recursion pt.2
- [ ] Memoization, Caching & Closures
- [ ] Stacks & Queues

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->

---
transition: slide-left
---

# Review Recursion Exercises
Write recursive functions for the following problems. 

1. Write a function that computes: n to the exponent x
   - ex: `power(2, 3)` // should output 8
2. Calculate the sum of natural number up to n
   - ex: `sum(5) // should output 15`
3. Write a function that computes the nth Fibonacci number (1, 1, 2, 3, 5, 8, ...)
   - ex: `fibonacci(5) // should output 5`
4. Write a function that reverses a string
   - ex: `reverse("hello") // should output "olleh"`
5. Write a function that checks if a string is a palindrome (reads the same forwards and backwards)
   - ex: `isPalindrome("racecar") // should output true`

---
transition: slide-left
---

# Binary Sort using Recursion Flowchart


<img src="/assets/binflow.png" width="750">


---
transition: slide-left
---

# Binary Sort using Recursion (pg.2)

- if arr.length is 0 return false
- if midpoint is n return true
- if n < middle index then search left side
- if n > middle index then search right side
```js
function binarySearch(arr, n, left = 0, right = arr.length - 1) {
    if (left > right) return -1;

    const mid = Math.floor((left + right) / 2);

    if (arr[mid] === n) return mid;
    else if (n < arr[mid]) {
        return binarySearch(arr, n, left, mid - 1); // Search left half
    } else {
        return binarySearch(arr, n, mid + 1, right); // Search right half
    }
}
```

---
transition: slide-left
---


# Memoizing using a basic cache for Fibonnaci

---
transition: slide-left
---

# Intro to Closures

---
transition: slide-left
---

# Memoizing using a closure for Fibonnaci



---
layout: image-right
transition: slide-left
image: /assets/recursion.png
backgroundSize: 400px 400px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:
- 🗼 [Tower of Hanoi](https://www.youtube.com/watch?v=rf6uf3jNjbo)
- 👀 [Visual Go](https://visualgo.net/en)
- 💫 [Data Structure Visualization](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)


---
transition: slide-left
---

# Stacks

- an ordered collection of items
- Fast insert and removal `O(1)`
- LIFO (Last In First Out)
- limited access to data via `pop() push()`

<img src="/assets/stack.webp" width="500" style="background-color: #fff; display: block; margin: 0 auto;">


---
transition: slide-left
---

# Stack: Methods

| Method                 | Description                                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `push(item)` | Adds an item to the top of the stack.                                                                                            |
| `pop()`      | Removes and returns the item at the top of the stack. Often throws an error or returns `null`/`undefined` if the stack is empty. |
| `isEmpty()`            | Returns `true` if the stack has no elements, `false` otherwise.                                                   |
| `peek()`     | Returns the item at the top of the stack **without** removing it. Useful for checking the next item to be popped. |
| `size()`               | Returns the number of elements in the stack.                                                                      |
| `print()` (optional)   | Displays the contents of the stack, often for debugging                               |


---
transition: slide-left
---

# How would you use Linked Lists to build a Stack? (pg.1)
1. Create a Node class
  ```md
  Class Node:
      value
      next
  ```
2. Create a Stack class
  ```md
  Class Stack:
      top = null   // Points to the top node
      size = 0     // Optional: tracks number of elements
  ```
3. Push
  ```md
  Method push(value):
      Create a new node with the given value
      Set new node's next to current top
      Update top to be the new node
      Increment size
  ```

---
transition: slide-left
---

# How would you use Linked Lists to build a Stack? (pg.2)

4.
  ```md
  Method pop():
      If stack is empty (top is null), return error or null
      Store value from top node
      Set top to top.next (removes the first node)
      Decrement size
      Return stored value
  ```
5. 
  ```md
  Method peek():
      If stack is empty, return error or null
      Return top.value
  ```
6.
  ```md
  Method size():
      Return the size counter
  ```

---
transition: slide-left
---

# Queues

- an ordered collection of items
- Fast insert and removal `O(1)`
- FIFO (First In First Out)
- limited access to data via `dequeue() enqueue()`

<img src="/assets/queue.png" width="500" style="background-color: #fff; display: block; margin: 0 auto;">

---
transition: slide-left
---

# Queue: Methods

| Method          | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| `enqueue(item)` | Adds an item to the **back/rear** of the queue.             |
| `dequeue()`     | Removes and returns the item at the **front** of the queue. |
| `isEmpty()`            | Returns `true` if the queue has no elements.             |
| `peek()`   | Returns the item at the **front** without removing it.   |
| `size()`               | Returns the number of elements in the queue.             |
| `print()` (optional) | Converts the queue to an array for inspection/debugging. |

---
transition: slide-left
---

# How would you use Linked Lists to build a Queue?

---
transition: slide-left
---

# Homework

- Work on your "Note-taking" midterm app due June 15 midnight EST
   - can submit before due date if you wish
- Recursion exercises: https://leetcode.com/problem-list/recursion/