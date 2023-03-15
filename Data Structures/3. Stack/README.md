# Stacks in C++

### What is a stack?
* A stack is a data structure that stores a collection of elements in a **last-in, first-out (LIFO)** order. 
* In other words, the element that is inserted last is the first one to be removed.

### Creating a stack
In C++, you can create a stack using the stack class from the **Standard Template Library (STL).**

```c++
#include <stack>

std::stack<int> s; // creates an empty stack of integers
```

### Pushing elements onto a stack
You can push elements onto a stack using the push function.

```c++
s.push(10); // pushes the integer 10 onto the stack
s.push(20); // pushes the integer 20 onto the stack
```

### Popping elements from a stack
You can pop elements from a stack using the pop function.

```c++
s.pop(); // removes the top element (20) from the stack
```

### Accessing the top element of a stack
You can access the top element of a stack using the top function.

```c++
int top_element = s.top(); // returns the top element (10) of the stack
```

### Checking if a stack is empty
You can check if a stack is empty using the empty function.

```c++
bool is_empty = s.empty(); // returns false if the stack is not empty
```

### Conclusion
Stacks are a useful data structure in C++ that allow you to store and manipulate a collection of elements in a last-in, first-out (LIFO) order.
By understanding how to create, push, pop, access, and check if a stack is empty, you can use stacks effectively in your programs.
