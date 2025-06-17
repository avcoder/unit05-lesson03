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
- [ ] Memoization & Closures
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
layout: center
---

# Could there be a way to optimize our functions?
ex: more performant not to re-calculate fibonnaci(5) repeatedly if previously calculated/memorized

---
transition: slide-left
---

# Binary Search using Recursion Flowchart


<img src="/assets/binflow.png" width="750">


---
transition: slide-left
---

# Binary Search using Recursion (pg.2)

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

# Big O for Binary Search

| **Aspect**              | **Sorted Array or [Tree](https://www.enjoyalgorithms.com/static/sorted-array-to-balanced-bst-9475114a48f6ab0a466a3dbdc8da0343.png)**          |
| ----------------------- | ------------------------- |
| **Best Case**           | O(1)                      |
| **Average Case**        | O(log n)                  |
| **Worst Case**          | O(log n)                  |

- refer to [Big O cheatsheet](https://www.bigocheatsheet.com/)

---
transition: slide-left
layout: center
---

# Could there be a way to optimize our functions?
ex: more performant not to re-calculate fibonnaci(5) repeatedly if previously calculated/memorized


---
transition: slide-left
layout: center
class: text-center
---

# What is a Cache?
A cache is a storage layer that temporarily holds data to serve future requests faster.  

ex: saving data to an object/array

---
transition: slide-left
layout: center
class: text-center
---

# What is a Memoization?
A specific kind of caching used in functions to store results of expensive computations.

It's caching a function's input (key) with its result (value)

---
transition: slide-left
---

# Cache vs Memoization

| Feature               | **Cache**                                             | **Memoization**                                        |
| --------------------- | ----------------------------------------------------- | ------------------------------------------------------ |
| **Definition**        | A general-purpose storage for reused data             | A specialized form of caching for function results     |
| **Purpose**           | Speeds up access to data or resources                 | Speeds up repeated function calls with the same inputs |
| **Scope**             | Broad: system-level, application-level, network, etc. | Narrow: typically used in pure functions               |
| **Use Case Examples** | Web page caching, database query caching, CPU cache   | Recursive functions like `fibonacci(n)`                |

- see React hook [useCallback](https://react.dev/reference/react/useCallback)
- see React hook [useMemo](https://react.dev/reference/react/useMemo)

---
transition: slide-left
---

# Memoization Goal

```js
const factorial = (n) => {
  // pretend we have code here to calculate n * (n-1) * (n-2) ... * (1)
}

// here we ask to run factorial on input 35 which it calculates
factorial(35) 

// then wouldn't it be cool if factorial function remembered previous result of factorial(35)?
// such that it wouldn't have to work as hard to calculate: factorial(36)
// ex: factorial(35) * 36 means simply recalling what factorial(35) previously gave us
factorial(36) 
```

---
transition: slide-left
---

# Intro to Closures
A closure is a function that remembers the variables from its outer (enclosing) function scope, even after the outer function has finished executing.

```js
function outerFunction() {
  let outerVariable = 'I am from outer scope';

  function innerFunction() {
    console.log(outerVariable); // <-- has access to outerVariable
  }

  return innerFunction;
}

const myClosure = outerFunction(); // outerFunction has finished
myClosure(); // Output: "I am from outer scope"
```

- outerFunction is called and returns innerFunction.
- Even though outerFunction has finished executing, innerFunction still remembers outerVariable.
- That’s a closure.

---
transition: slide-left
---

# Memoizing using a closure for Fibonacci

```js
const fib = (function() {
  const memo = {};

  function fibonacci(n) {
    if (n < 0) throw new Error("Fibonacci is not defined for negative numbers.");
    if (n === 0) return 0;
    if (n === 1) return 1;
    
    if (memo[n] !== undefined) {
      return memo[n];
    }

    memo[n] = fibonacci(n - 1) + fibonacci(n - 2);
    return memo[n];
  }

  return f;
})();
```

---
transition: slide-left
---

# Big O for Recursive Fibonacci using Memoization

| Operation                   | Time |
| --------------------------- | ---- |
| First-time compute `fib(n)` | O(n) |
| Subsequent lookup           | O(1) |



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

# Big O for Stacks using Linked List

| **Operation** | **Time Complexity** | **Explanation**                        |
| ------------- | ------------------- | -------------------------------------- |
| `push`        | O(1)                | Insert at the head of the list.        |
| `pop`         | O(1)                | Remove from the head of the list.      |
| `peek`        | O(1)                | Access the head without removing it.   |
| `isEmpty`     | O(1)                | Check if head is `null`.               |
| `size`        | O(1)\*              | Constant if a size counter is tracked. |

*If you don't maintain a size counter, size would be O(n).


---
transition: slide-left
---

# Stack Usage

```js
// Example usage:
const stack = new Stack();
stack.push(10);
stack.push(20);
stack.push(30);

console.log(stack.peek());    // Output: 30
console.log(stack.pop());     // Output: 30
console.log(stack.getSize()); // Output: 2
```

---
transition: slide-left
---

# Pseudocode - Stack via Linked List (pg.1)
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

# Pseudocode - Stack via Linked List (pg.2)

4. Pop
  ```md
  Method pop():
      If stack is empty (top is null), return error or null
      Store value from top node
      Set top to top.next (removes the first node)
      Decrement size
      Return stored value
  ```
5. Peek
  ```md
  Method peek():
      If stack is empty, return error or null
      Return top.value
  ```
6. isEmpty
  ```md
  Method isEmpty():
     Return if stack is empty
  ```
7. Size
  ```md
  Method size():
      Return the size counter
  ```

---
transition: slide-left
---

# Exercise: Let's build out a Stack using Linked List
see [Visualization](https://www.cs.usfca.edu/~galles/visualization/StackLL.html)

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.top = null;   // Points to the top of the stack
    this.size = 0;     // Tracks the number of elements
  }

  push(value) { /* ?? */ }

  pop() { /* ?? */ }

  peek() { /* ?? */ }

  isEmpty() { /* ?? */ }

  getSize() { /* ?? */ }
}
```

<!-- 
- push
   - const newNode = new Node(value)
   - newNode.next = this.top
   - this.top = newNode
   - this.size++

- pop
- if (this.isEmpty()) { throw new Error("Stack underflow - The stack is empty") }
   - const poppedValue = this.top.value
   - this.top = this.top.next
   - this.size--
   - return poppedValue

- peek
   - if (this.isEmpty()) { return null }
   - return this.top.value

- isEmpty
   - return this.top === null

- size
   - return this.size
-->

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

# Big O for Queues using Linked List

| **Operation** | **Time Complexity** | **Explanation**                               |
| ------------- | ------------------- | --------------------------------------------- |
| `enqueue`     | O(1)                | Insert at the tail (requires `tail` pointer). |
| `dequeue`     | O(1)                | Remove from the head.                         |
| `peek`        | O(1)                | Access the head without removing it.          |
| `isEmpty`     | O(1)                | Check if head is `null`.                      |
| `size`        | O(1)\*              | Constant if a size counter is maintained.     |

*If you don't maintain a size counter, size would be O(n).


---
transition: slide-left
---

# Queue Usage

```js
const queue = new Queue();
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);

console.log(queue.peek());    // Output: 1
console.log(queue.dequeue()); // Output: 1
console.log(queue.getSize()); // Output: 2
```

---
transition: slide-left
---

# Pseudocode - Queue via Linked List (pg.1)
1. Create a Node class
  ```md
  Class Node:
    value
    next
  ```
2. Create a Queue class
  ```md
  Class Queue:
    front = null
    rear = null
    size = 0
  ```
3. Enqueue
  ```md
  Method enqueue(value):
    Create a new node with the given value
    If the queue is empty (front is null):
        Set both front and rear to the new node
    Else:
        Set rear.next to the new node
        Update rear to point to the new node
    Increment size
  ```

---
transition: slide-left
---

# Pseudocode - Queue via Linked List (pg.2)

4. Dequeue
  ```md
  Method dequeue():
    If the queue is empty (front is null), return error or null
    Store the value from the front node
    Set front to front.next
    If front becomes null (queue is now empty):
        Also set rear to null
    Decrement size
    Return stored value
  ```
5. Peek
  ```md
  Method peek():
    If the queue is empty, return error or null
    Return front.value
  ```
6. Size
  ```md
  Method size():
    Return the size counter
  ```

---
transition: slide-left
---

# Exercise: Build out a Queue using a Linked List
see [Visualization](https://www.cs.usfca.edu/~galles/visualization/QueueLL.html)

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Queue {
  constructor() {
    this.front = null; // Points to the front (head) of the queue
    this.rear = null;  // Points to the end (tail) of the queue
    this.size = 0;
  }

  enqueue(value) { /* ?? */ }

  dequeue() { /* ?? */ }

  peek() { /* ?? */ }

  isEmpty() { /* ?? */ }

  getSize() { /* ?? */ }
}
```

<!--
- enqueue
   - const newNode = new Node(value);
   - if (this.isEmpty()) {
      - this.front = this.rear = newNode;
   - } else {
      - this.rear.next = newNode;
      - this.rear = newNode;
   - }
   - this.size++;

- dequeue
   - if (this.isEmpty()) {
      - throw new Error("Queue underflow - The queue is empty");
   - }
   - const dequeuedValue = this.front.value;
   - this.front = this.front.next;
   - if (!this.front) {
      - this.rear = null; // Queue is now empty
   - }
   - this.size--;
   - return dequeuedValue;
-->

---
transition: slide-left
---

# Homework

- Khan Academy: https://www.khanacademy.org/computing/computer-science/algorithms
- Leetcode Queues: https://leetcode.com/problem-list/queue/
- Leetcode Stacks: https://leetcode.com/problem-list/stack/