# Queue 
A stack is a linear data structure that follows the **LIFO (Last-In-First-Out)** principle. It means that the last element inserted into the stack is the first element to be removed.

### Implementation
* We can implement a stack using an array or a linked list. Here, we will discuss the implementation using an array.
* To implement a stack using an array, you need to declare a stack class with a fixed size array and a top index variable that will keep track of the top element of the stack.

```cpp
class Stack {
private:
    int top;
    int capacity;
    int* arr;
public:
    Stack(int size);
    ~Stack();
    bool isFull();
    bool isEmpty();
    void push(int value);
    int pop();
};
```

The **`top`** variable will initially be set to -1, indicating that the stack is empty. The **`capacity`** variable will determine the maximum number of elements that the stack can hold. The **`arr`** pointer will point to the dynamic array that will hold the stack elements.

### Constructor
The constructor of the **`Stack`** class will initialize the **`top`** and **`capacity`** variables and allocate memory for the array.

```cpp
Stack::Stack(int size) {
    top = -1;
    capacity = size;
    arr = new int[capacity];
}
```

### Destructor
The destructor will free up the memory allocated for the array.

```cpp
Stack::~Stack() {
    delete[] arr;
}
```

### Push operation
The **`push`** function will insert a new element at the top of the stack. It first checks if the stack is full or not. If the stack is not full, it increments the **`top`** variable and assigns the new element to the next available position in the array.

```cpp
void Stack::push(int value) {
    if (isFull()) {
        throw "Stack is full!";
    }
    arr[++top] = value;
}
```

### Pop operation
The **`pop`** function will remove and return the top element of the stack. It first checks if the stack is empty or not. If the stack is not empty, it returns the top element and decrements the **`top`** variable.

```cpp
int Stack::pop() {
    if (isEmpty()) {
        throw "Stack is empty!";
    }
    return arr[top--];
}
```

### isEmpty and isFull operations
The **`isEmpty`** and **`isFull`** functions will check if the stack is empty or full, respectively.

```cpp
bool Stack::isEmpty() {
    return top == -1;
}

bool Stack::isFull() {
    return top == capacity - 1;
}
```

### Conclusion
In summary, a stack is a useful data structure that can be implemented in C++ using an array. The stack class should include operations to push, pop, check if the stack is empty or full, and a constructor and destructor to allocate and free up memory, respectively.
