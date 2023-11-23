## Selection sort

geeksforgeeks: [Selection sort](https://www.geeksforgeeks.org/selection-sort/)

### summary

Selection sort is a simple and efficient sorting algorithm that works by repeatedly selecting the smallest (or largest) element from the unsorted portion of the list and moving it to the sorted portion of the list.

##### selection sort algorithm follows like this:

The algorithm repeatedly selects the smallest (or largest) element from the unsorted portion of the list and swaps it with the first element of the unsorted part. This process is repeated for the remaining unsorted portion until the entire list is sorted.

##### complexity

time complexity: o(n^2) \
space complexity: o(1)

### details

language: **c**

### code snippets

#### solution 1:

my/community solution\
time complexity: o(n^2) \
space complexity: o(1)

```
void swapPlaces(int* arr, int i, int j){
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}


void selectionSort(int arr[], int n)
{
    int minEl;
    int minElInd;
    int* arrPtr = &arr[0];
    for(int i = 0; i < n; i++){
        minElInd = i;
        minEl = arr[i];
        for(int j = i + 1; j < n; j++){
            if(arr[j] < minEl){
                minEl = arr[j];
                minElInd = j;
            }
        }
        swapPlaces(arrPtr, i, minElInd);
    }
}
```
