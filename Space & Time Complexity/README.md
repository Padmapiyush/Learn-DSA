
# Space & Time Complexity

Space and time complexity analysis is an important aspect of designing and analyzing algorithms in computer science. Here are some notes on space and time complexity in C++:

## Space Complexity :minidisc:
Space complexity refers to the amount of memory required by an algorithm to solve a problem.

* In C++, space complexity can be analyzed by considering the data structures used by the algorithm and the size of the input data.

* The space complexity of an algorithm is often expressed in terms of the "big O" notation, which provides an upper bound on the amount of memory used by the algorithm.

* For example, if an algorithm uses an array of size n, the space complexity is O(n), which means that the algorithm uses a linear amount of memory with respect to the input size.

* In general, the space complexity of an algorithm should be minimized to conserve memory resources, especially in situations where memory is limited.

| Notation |	Name |	Examples of algorithms or data structures |
|-------|-------|--------------------------------------------|
O(1)| Constant space| independent of the size of the input.
O(n)| Linear space| space complexity increases linearly with the size of the input.
O(n^2)| Quadratic space| common for two-dimensional arrays or nested loops.
O(log n)| Logarithmic space| usually achieved by recursive algorithms with small stacks.
O(n log n)| Quasilinear space| common for efficient sorting algorithms.
O(2^n)| Exponential space| common for brute-force search algorithms.
O(n!)| Factorial space| common for brute-force permutation algorithms.

### Space Complexity Tricks :sparkles:
- Use the smallest data type possible to store your data.
- Avoid using unnecessary data structures or variables.
- Reuse memory when possible instead of creating new objects.
- Use dynamic memory allocation sparingly and free memory as soon as it is no longer needed.
- Avoid recursion when possible as it can use a lot of memory.

## Time Complexity :hourglass:
Time complexity refers to the amount of time required by an algorithm to solve a problem.

* In C++, time complexity can be analyzed by considering the number of operations performed by the algorithm and the size of the input data.

* The time complexity of an algorithm is also expressed using the big O notation, which provides an upper bound on the amount of time required by the algorithm.

* For example, if an algorithm takes n steps to solve a problem, the time complexity is O(n), which means that the algorithm takes a linear amount of time with respect to the input size.

* In general, the time complexity of an algorithm should be minimized to conserve computational resources, especially in situations where processing power is limited.

* The choice of algorithm can have a significant impact on the time complexity, and it is important to choose the most efficient algorithm for a given problem.

| Notation |	Name |	Examples of algorithms or data structures |
|-------|-------|--------------------------------------------|
O(1)| Constant time| independent of the size of the input.
O(log n)| Logarithmic time| usually achieved by divide and conquer algorithms.
O(n)| Linear time| time complexity increases linearly with the size of the input.
O(n log n)| Quasilinear time| common for efficient sorting algorithms.
O(n^2)| Quadratic time| common for nested loops or inefficient sorting algorithms.
O(n^3)| Cubic time| common for nested loops in three-dimensional arrays.
O(2^n)| Exponential time| common for brute-force search algorithms.
O(n!)| Factorial time | common for brute-force permutation algorithms.

### Time Complexity Tricks :sparkles:
- Use built-in functions instead of writing your own algorithms, as they are often optimized for performance.
- Avoid nested loops whenever possible, as they increase the time complexity exponentially.
- Use dynamic programming techniques to solve problems that can be broken down into smaller subproblems.
- Use binary search to search for elements in a sorted array, as it has a time complexity of O(log n).
- Use hash tables to store and retrieve data quickly, as they have an average time complexity of O(1).
- Use memoization to cache the results of expensive computations, reducing the time complexity of the algorithm.

## Cheatsheet for space and time complexity in C++ :

|Data Structure|	Access|	Search|	Insertion|	Deletion|	Space|
|-----|-----|------|-------|--------|--------|
Array |	O(1) |	O(n) |	O(n) |	O(n)	|O(n)
Dynamic Array |	O(1) |	O(n) |	O(n) |	O(n) |	O(n)
Linked List |	O(n) | 	O(n) |	O(1) |	O(1) |	O(n)
Stack |	O(1) |	O(n) |	O(1) |	O(1) |	O(n)
Queue |	O(1) |	O(n) |	O(1) |	O(1) |	O(n)
Binary Search Tree |	O(log n) |	O(log n) |	O(log n) |	O(log n) |	O(n)
Hash Table |	O(1) |	O(1) |	O(1) |	O(1) |	O(n)
Heap |	O(1) |	O(n) |	O(log n) |	O(log n) |	O(n)


# Tips :bulb:
**1. Avoid nested loops:** <br>
- When analyzing the time complexity of an algorithm, nested loops are a common source of inefficiency. 
- Each additional nested loop can multiply the number of operations required by the algorithm, so it's important to identify and count these loops carefully.

**2. Count operations, not lines of code:**<br>
- When analyzing the time complexity of an algorithm, it's important to focus on the number of operations that the algorithm performs, rather than the number of lines of code that it contains. 
- Some lines of code may perform many operations, while others may perform only a few, so counting lines of code can be misleading.

**3. Use the "Big O" notation:**<br>
- The Big O notation is a way of expressing the upper bound of an algorithm's time or space complexity. 
- When analyzing the time or space complexity of an algorithm, it's important to express the complexity in terms of Big O notation, as this gives a standardized way of comparing different algorithms.

**4. Beware of recursion:**<br>
- Recursive algorithms can be difficult to analyze for time and space complexity, as each recursive call can add additional memory usage and operations. 
- It's important to carefully analyze the recursion depth and the operations performed by each recursive call when analyzing the complexity of recursive algorithms.

**5. Sort data before searching:**
-When searching for data in a collection, sorting the collection beforehand can greatly reduce search time complexity.
-For example, binary search on a sorted array has time complexity O(log n), while linear search on an unsorted array has time complexity O(n).

**6. Experiment with different input sizes:**
- When analyzing the time and space complexity of an algorithm, it's important to test the algorithm with different input sizes to get a better sense of how the complexity scales with the input size. 
- This can help to identify bottlenecks and optimize the algorithm for specific input sizes.












































