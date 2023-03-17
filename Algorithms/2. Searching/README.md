# Linear Search algorithm 
Linear Search algorithm is a simple search algorithm that works by sequentially checking each element of an array or a list until a match is found. It has a time complexity of `O(n)`, where `n` is the number of elements in the array.

### Algorithm:

1. Start from the first element of the array.
2. Compare the target element with the current element of the array.
3. If the target element is found, return its index.
4. If the target element is not found, move to the next element in the array and repeat step 2 and 3 until the end of the array is reached.
5. If the end of the array is reached and the target element is not found, return -1 or any other sentinel value to indicate that the element was not found.

Here's a sample code in C++ for Linear Search Algorithm:

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i; // return the index where the target element is found
        }
    }
    return -1; // return -1 if the target element is not found
}

int main() {
    int arr[] = { 4, 6, 2, 9, 1, 5 };
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 9;
    int result = linearSearch(arr, size, target);
    if (result == -1) {
        cout << "Element not found." << endl;
    }
    else {
        cout << "Element found at index " << result << endl;
    }
    return 0;
}
```

In the above code, we define a function called `linearSearch` that takes an array `arr`, its size `size`, and the target element target as input. The function returns the index of the target element if it is found in the array, otherwise, it returns `-1`.

In the main function, we create an array `arr` with 6 elements, and we search for the element 9 using the `linearSearch` function. If the element is found, we print its index, otherwise, we print a message saying that the element was not found.

# Binary Search algorithm
Binary Search algorithm is a search algorithm that works by repeatedly dividing the search interval in half until the target element is found. It can be applied only to sorted arrays or lists. It has a time complexity of `O(log n)`, where `n` is the number of elements in the array.

### Algorithm:

1. Sort the array or list in ascending or descending order.
2. Define the search interval as the entire array or list.
3. If the target element is equal to the middle element of the search interval, return the index of the middle element.
4. If the target element is less than the middle element of the search interval, repeat the search on the left half of the search interval.
5. If the target element is greater than the middle element of the search interval, repeat the search on the right half of the search interval.
6. If the target element is not found, return -1 or any other sentinel value to indicate that the element was not found.

Here's a sample code in C++ for Binary Search Algorithm:

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int size, int target) {
    int low = 0;
    int high = size - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target) {
            return mid; // return the index where the target element is found
        }
        else if (arr[mid] < target) {
            low = mid + 1; // search in the right half of the search interval
        }
        else {
            high = mid - 1; // search in the left half of the search interval
        }
    }
    return -1; // return -1 if the target element is not found
}

int main() {
    int arr[] = { 1, 2, 4, 5, 6, 9 };
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 6;
    int result = binarySearch(arr, size, target);
    if (result == -1) {
        cout << "Element not found." << endl;
    }
    else {
        cout << "Element found at index " << result << endl;
    }
    return 0;
}
```

In the above code, we define a function called `binarySearch` that takes an array `arr`, its size `size`, and the target element `target` as input. The function returns the index of the target element if it is found in the array, otherwise, it returns `-1`.

In the `main` function, we create a sorted array `arr` with 6 elements, and we search for the element 6 using the `binarySearch` function. If the element is found, we print its index, otherwise, we print a message saying that the element was not found.









































































