## Bubble Sort

GeeksForGeeks: [Bubble Sort](https://www.geeksforgeeks.org/bubble-sort/)

### Summary

Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in the wrong order. This algorithm is not suitable for large data sets as its average and worst-case time complexity is quite high. \

##### Bubble Sort algorithm follows like this:

- Traverse from left and compare adjacent elements and the higher one is placed at right side.
  - Meaning while traversing we take two elements at a time and swap them if right one is bigger else we move on.
- In this way, the largest element is moved to the rightmost end at first.
- This process is then continued to find the second largest and place it and so on until the data is sorted.
  - Meaning after first iteration is done i.e. larget element is moved to the right most end, we do the second iteration till second last element as the last one is already sorted.

##### Complexity

Time Complexity: O(n^2) \
Space Complexity: O(1)

### Details

Language: **C**

### Code Snippets

#### Solution 1:

My Solution\
Time Complexity: O(n^2) \
Space Complexity: O(1)

```
// Optimized implementation of Bubble sort
#include <stdbool.h>
#include <stdio.h>

// helper swapping method for Bubble sort
void swap(int* arr, int i, int j){
	int temp = arr[i];
  	arr[i] = arr[j];
  	arr[j] = temp;
}

// Main method for Bubble Sort
void bubbleSort(int arr[], int n)
{
  	int j = n - 1;
  	int* arrPtr = &arr[0];
	while(j >= 0){
    	for(int temp = 0; temp < j; temp++){
          	if(arr[temp] > arr[temp + 1])
        		swap(arrPtr, temp, temp + 1);
        }
      	j--;
    }
}

// Function to print an array
void printArray(int arr[], int size)
{
	int i;
	for (i = 0; i < size; i++)
		printf("%d ", arr[i]);
}

// Driver program to test above functions
int main()
{
	int arr[] = { 64, 34, 25, 12, 22, 11, 90 };
	int n = sizeof(arr) / sizeof(arr[0]);
	bubbleSort(arr, n);
	printf("Sorted array: \n");
	printArray(arr, n);
	return 0;
}
```

#### Solution 2:

Community Solution: Slightly more optimized\
Time Complexity: O(n^2) \
Space Complexity: O(1)

```
// Optimized implementation of Bubble sort
#include <stdbool.h>
#include <stdio.h>

void swap(int* xp, int* yp)
{
	int temp = *xp;
	*xp = *yp;
	*yp = temp;
}

// An optimized version of Bubble Sort
void bubbleSort(int arr[], int n)
{
	int i, j;
	bool swapped;
	for (i = 0; i < n - 1; i++) {
		swapped = false;
		for (j = 0; j < n - i - 1; j++) {
			if (arr[j] > arr[j + 1]) {
				swap(&arr[j], &arr[j + 1]);
				swapped = true;
			}
		}

		// If no two elements were swapped by inner loop,
		// then break
		if (swapped == false)
			break;
	}
}

// Function to print an array
void printArray(int arr[], int size)
{
	int i;
	for (i = 0; i < size; i++)
		printf("%d ", arr[i]);
}

// Driver program to test above functions
int main()
{
	int arr[] = { 64, 34, 25, 12, 22, 11, 90 };
	int n = sizeof(arr) / sizeof(arr[0]);
	bubbleSort(arr, n);
	printf("Sorted array: \n");
	printArray(arr, n);
	return 0;
}

```
