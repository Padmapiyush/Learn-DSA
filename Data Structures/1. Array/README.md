# Arrays in C++
### What is an array?
An array is a collection of elements of the same data type. Each element in the array is identified by an index or a subscript.

### Declaring an array
In C++, you can declare an array by specifying the data type of the elements and the number of elements in the array.<br>
```C++
int arr[5]; // declares an integer array with 5 elements
```

### Initializing an array
You can initialize an array at the time of declaration by specifying the values inside curly braces.<br>
```C++
int arr[5] = {1, 2, 3, 4, 5}; // initializes an integer array with 5 elements
```

### Accessing array elements
You can access array elements using their index or subscript.<br>
```C++
int arr[5] = {1, 2, 3, 4, 5};

cout << arr[0] << endl; // prints the first element of the array
cout << arr[3] << endl; // prints the fourth element of the array
```

### Changing array elements
You can change the value of an array element by assigning a new value to it using its index.<br>
```C++
int arr[5] = {1, 2, 3, 4, 5};

arr[2] = 10; // changes the value of the third element to 10

cout << arr[2] << endl; // prints 10
```

### Array size
You can get the number of elements in an array by using the sizeof operator.<br>
```C++
int arr[5] = {1, 2, 3, 4, 5};

cout << sizeof(arr) / sizeof(arr[0]) << endl; // prints 5
```

### Conclusion:
Arrays are a useful data structure in C++ that allow you to store multiple elements of the same data type.<br>
By understanding how to declare, initialize, and access array elements, you can use arrays effectively in your programs















