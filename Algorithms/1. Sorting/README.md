# Sorting Algorithms

## 1. Bubble Sort
Bubble sort is a `simple` sorting algorithm that repeatedly steps through the list, compares adjacent elements and swaps them if they are in the wrong order. Here are some notes and an example code in C++:

### Algorithm:
1. Start from the beginning of the list.
2. Compare each pair of adjacent elements.
3. If they are in the wrong order, swap them.
4. Continue until the end of the list.
5. Repeat steps 1-4 until no more swaps are needed.

Example Code:
```c++
void bubbleSort(int arr[], int n) {
   for (int i = 0; i < n-1; i++) { // loop through the array
      for (int j = 0; j < n-i-1; j++) { // compare adjacent elements
         if (arr[j] > arr[j+1]) { // swap if they are in the wrong order
            int temp = arr[j];
            arr[j] = arr[j+1];
            arr[j+1] = temp;
         }
      }
   }
}
```
The time complexity of bubble sort is `O(n^2)`, which makes it inefficient for large data sets. However, it is `simple` and `easy to understand`, making it a `good choice for small data sets` or educational purposes.

## 2. Insertion Sort
Insertion sort is a `simple` sorting algorithm that builds the final sorted array one item at a time. Here are some notes and an example code in C++:

### Algorithm:

1. Start from the second element of the list.
2. Compare the current element with the sorted sub-list to its left.
3. If the current element is smaller, shift the larger elements one position to the right.
4. Insert the current element in the correct position.
5. Repeat steps 2-4 until the end of the list.

Example Code:
```c++
void insertionSort(int arr[], int n) {
   for (int i = 1; i < n; i++) { // loop through the array
      int key = arr[i]; // current element
      int j = i - 1;
      while (j >= 0 && arr[j] > key) { // compare with sorted sub-list
         arr[j+1] = arr[j]; // shift larger elements to the right
         j--;
      }
      arr[j+1] = key; // insert current element in the correct position
   }
}
```

The time complexity of insertion sort is `O(n^2)`, but it has a `good performance for small data sets` and is also `efficient for almost-sorted data sets`.

## 3. Selection sort 
Selection sort is a `simple` sorting algorithm that works by selecting the smallest (or largest) element from the unsorted part of the list and moving it to the beginning (or end) of the sorted part of the list. Here are some notes and an example code in C++:

### Algorithm:

1. Start from the beginning of the list.
2. Find the smallest (or largest) element in the unsorted part of the list.
3. Swap it with the first (or last) element in the unsorted part of the list.
4. Move the boundary between the sorted and unsorted parts of the list one element to the right (or left).
5. Repeat steps 2-4 until the entire list is sorted.

Example Code:
```c++
void selectionSort(int arr[], int n) {
   for (int i = 0; i < n-1; i++) { // loop through the array
      int minIndex = i; // index of smallest element
      for (int j = i+1; j < n; j++) { // find the smallest element
         if (arr[j] < arr[minIndex]) {
            minIndex = j;
         }
      }
      // swap the smallest element with the first element in the unsorted part of the list
      int temp = arr[minIndex];
      arr[minIndex] = arr[i];
      arr[i] = temp;
   }
}
```

The time complexity of selection sort is `O(n^2)`, but it has the advantage of making only `O(n)` swaps, which can be important if the cost of swapping elements is high. It is also an `in-place sorting algorithm`.

## 4. Quick sort 
Quick sort is a `divide-and-conquer sorting algorithm` that works by selecting a pivot element from the list, partitioning the other elements into two sub-lists based on whether they are less than or greater than the pivot, and then recursively sorting the sub-lists. Here are some notes and an example code in C++:

### Algorithm:

1. Select a pivot element from the list.
2. Partition the other elements into two sub-lists, less than or equal to the pivot and greater than the pivot.
3. Recursively apply quick sort to each sub-list.
4. Combine the sorted sub-lists.

Example Code:

```c++
void quickSort(int arr[], int low, int high) {
   if (low < high) { // base case
      int pivot = partition(arr, low, high); // partition the list
      quickSort(arr, low, pivot-1); // sort the left sub-list
      quickSort(arr, pivot+1, high); // sort the right sub-list
   }
}

int partition(int arr[], int low, int high) {
   int pivot = arr[high]; // choose the last element as the pivot
   int i = low - 1; // index of smaller element
   for (int j = low; j <= high-1; j++) { // loop through the list
      if (arr[j] <= pivot) { // if current element is less than or equal to the pivot
         i++; // increment index of smaller element
         swap(arr[i], arr[j]); // swap the current element with the smaller element
      }
   }
   swap(arr[i+1], arr[high]); // swap the pivot with the next element
   return i+1; // return the index of the pivot
}
```

The time complexity of quick sort is `O(nlogn)` on average and `O(n^2)` in the worst case (when the list is already sorted or nearly sorted and a bad pivot is chosen). However, it has `good performance for large data sets` and is widely used in practice.

## 5. Merge Sort
Merge sort is a `divide-and-conquer sorting algorithm` that works by dividing the list into two halves, recursively sorting each half, and then merging the sorted halves back together. Here are some notes and an example code in C++:

### Algorithm:

1. Divide the list into two halves.
2. Recursively apply merge sort to each half.
3. Merge the sorted halves back together.

Example Code:

```c++
void mergeSort(int arr[], int left, int right) {
   if (left < right) { // base case
      int mid = (left + right) / 2; // calculate the middle index
      mergeSort(arr, left, mid); // sort the left half
      mergeSort(arr, mid+1, right); // sort the right half
      merge(arr, left, mid, right); // merge the sorted halves
   }
}

void merge(int arr[], int left, int mid, int right) {
   int n1 = mid - left + 1; // size of left sub-array
   int n2 = right - mid; // size of right sub-array
   int L[n1], R[n2]; // temporary arrays
   for (int i = 0; i < n1; i++) { // copy the left sub-array
      L[i] = arr[left + i];
   }
   for (int j = 0; j < n2; j++) { // copy the right sub-array
      R[j] = arr[mid + 1 + j];
   }
   int i = 0, j = 0, k = left;
   while (i < n1 && j < n2) { // merge the sub-arrays
      if (L[i] <= R[j]) {
         arr[k] = L[i];
         i++;
      } else {
         arr[k] = R[j];
         j++;
      }
      k++;
   }
   while (i < n1) { // copy any remaining elements in the left sub-array
      arr[k] = L[i];
      i++;
      k++;
   }
   while (j < n2) { // copy any remaining elements in the right sub-array
      arr[k] = R[j];
      j++;
      k++;
   }
}
```

The time complexity of merge sort is `O(nlogn)` in all cases, but it `requires additional memory` for the temporary arrays used in the merge step. However, it is a `stable sorting algorithm` and is widely used in practice.

## 6. Heap Sort
Heap sort is a `comparison-based sorting algorithm` that works by building a max heap (for ascending order) or min heap (for descending order) from the list, repeatedly extracting the top element and rebuilding the heap until the list is sorted. Here are some notes and an example code in C++:

### Algorithm:

Build a max heap (for ascending order) or min heap (for descending order) from the list.
Repeatedly extract the top element and rebuild the heap until the list is sorted.
Example Code:

```c++
void heapSort(int arr[], int n) {
   // build max heap
   for (int i = n/2 - 1; i >= 0; i--) {
      heapify(arr, n, i);
   }
   // extract elements from the heap
   for (int i = n-1; i >= 0; i--) {
      swap(arr[0], arr[i]); // swap the top element with the last element
      heapify(arr, i, 0); // rebuild the heap
   }
}

void heapify(int arr[], int n, int i) {
   int largest = i; // initialize largest as root
   int left = 2*i + 1; // left child
   int right = 2*i + 2; // right child
   // check if left child is larger than root
   if (left < n && arr[left] > arr[largest]) {
      largest = left;
   }
   // check if right child is larger than largest
   if (right < n && arr[right] > arr[largest]) {
      largest = right;
   }
   // swap the root with the largest element
   if (largest != i) {
      swap(arr[i], arr[largest]);
      heapify(arr, n, largest); // recursively heapify the affected sub-tree
   }
}
```

The time complexity of heap sort is `O(nlogn)` in all cases, and it has `good performance for large data sets`. However, it is `not a stable sorting algorithm` and `requires additional memory` for the heap data structure.



































































